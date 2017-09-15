---
title: 'Error: Unable to Start Debugging on the Web Server | Microsoft Docs'
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: ae49f878ab0e361f7d49215669fab52fa3e6b06f
ms.contentlocale: es-es
ms.lasthandoff: 09/07/2017

---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: Unable to Start Debugging on the Web Server

When you try to debug an ASP.NET application running on a Web server, you may get this error message: `Unable to start debugging on the Web server`.

Often, this error occurs because an error or configuration change has occurred that requires an update to your Application Pools, an IIS reset, or both.

## <a name="specificerrors"></a>What is the detailed error message?

The `Unable to start debugging on the Web server` message is generic. Usually, a more specific message is included in the error string and that may help you identify the cause of the problem or search for a more exact fix. Here are a few of the more common error messages that are appended to the main error message:

- [IIS does not list a website that matches the launch url](#IISlist)
- [The web server is not configured correctly](#web_server_config)
- [Unable to connect to the webserver](#unabletoconnect)
- [The web server did not respond in a timely manner](#webservertimeout)
- [The microsoft visual studio remote debugging monitor(msvsmon.exe) does not appear to be running on the remote computer](#msvsmon)
- [Could not start ASP.NET debugging](#aspnet)
- [The debugger cannot connect to the remote computer](#cannot_connect)
- [See help for common configuration errors. Running the webpage outside of the debugger may provide further information.](#see_help)

## <a name="IISlist"></a> IIS does not list a website that matches the launch url

- Restart Visual Studio as an Administrator and retry debugging. (Some ASP.NET debugging scenarios require elevated privileges.)

    You can configure Visual Studio to always run as an Administrator by right-clicking the Visual Studio shortcut icon, choosing **Properties > Advanced**, and then choosing to always run as an Administrator.

## <a name="web_server_config"></a> The web server is not configured correctly

- See [Error: The web server is not configured correctly](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Unable to connect to the webserver

- Are you running Visual Studio and the Web server on the same machine and debugging using **F5** (instead of **Attach to Process**)? Open your project properties and make sure that the project is configured to connect to the correct Web server and launch URL. (Open **Properties > Web > Servers** or **Properties > Debug** depending on your project type.)

- If the Web server is remote, restart your Application Pool and then reset IIS. For more information, see [Check your IIS Configuration](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> The web server did not respond in a timely manner

- Reset IIS and retry debugging. Multiple debugger instances may be attached to the IIS process; a reset terminates them. For more information, see [Check your IIS Configuration](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> The microsoft visual studio remote debugging monitor(msvsmon.exe) does not appear to be running on the remote computer

- If you are debugging on a remote machine, make sure you have [installed and are running the remote debugger](../debugger/remote-debugging.md). If the message mentions a firewall, make sure the [correct ports in the firewall](../debugger/remote-debugger-port-assignments.md) are open, especially if you are using a third party firewall.
- If you are using a HOSTS file, make sure it is configured correctly. For example, if debugging using **F5** (instead of **Attach to Process**), the HOSTS file needs to include the same project URL as in your project properties, **Properties > Web > Servers** or **Properties > Debug**, depending on your project type.

## <a name="aspnet"></a> Could not start ASP.NET debugging

- Restart the Application Pool and reset IIS. For more information, see [Check your IIS Configuration](#vxtbshttpservererrorsthingstocheck).
- If you are doing URL rewrites, test a basic web.config with no URL rewrites. See the **Note** about the URL Rewrite Module in [Check your IIS Configuration](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> The debugger cannot connect to the remote computer

If you are debugging locally, this error may occur because Visual Studio is a 32-bit application, so it uses the 64-bit version of the remote debugger to debug 64-bit applications. Open your project properties and make sure that the project is configured to connect to the correct Web server and launch URL. (Open **Properties > Web > Servers** or **Properties > Debug** depending on your project type.)

Also, if you are using a HOSTS file, make sure it is configured correctly. For example, the HOSTS file needs to include the same project URL as in your project properties, **Properties > Web > Servers** or **Properties > Debug**, depending on your project type.

## <a name="see_help"></a> See help for common configuration errors. Running the webpage outside of the debugger may provide further information.

- Are you running Visual Studio and the Web server on the same machine? Open your project properties and make sure that the project is configured to connect to the correct Web server and launch URL. (Open **Properties > Web > Servers** or **Properties > Debug** depending on your project type.)

- If that does not work or you are debugging remotely, follow steps in [Check your IIS Configuration](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Check your IIS configuration

After taking steps detailed here to resolve the issue, and before trying again to debug, you may also need to reset IIS. You can do that by opening an Administrator command prompt and typing `iisreset`, or you can perform a reset in IIS Manager. 

* Stop and restart your IIS Application Pools, then retry. 

    The Application Pool may have stopped as a result of an error. Or, another configuration change that you made may require that you stop and restart your Application Pool.
    
    > [!NOTE]
    > If the Application Pool keeps stopping, you may need to uninstall the URL Rewrite Module from the Control Panel. You can reinstall it using the Web Platform Installer (WebPI). This issue may occur after a significant system upgrade.

* Check your Application Pool configuration, correct it if needed, and then retry.

    The Application Pool may be configured for a version of ASP.NET that does not match your Visual Studio project. Update the ASP.NET version in the Application Pool and restart it. For detailed information, see [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Also, if password credentials have changed, you may need to update them in your Application Pool or Web site.  In the Application Pool, update credentials in **Advanced Settings > Process Model > Identity**. For the Web site, update credentials in **Basic Settings > Connect as...**. Restart your Application Pool.
    
* Check that your Web Application folder has the right permissions.

    Make sure that you give IIS_IUSRS, IUSR, or the specific user associated with the Application Pool read and execute rights for the Web Application folder. Fix the issue and restart your Application Pool.

* Make sure that the correct version of ASP.NET is installed on IIS.

    Mismatched versions of ASP.NET on IIS and in your Visual Studio project may cause this issue. You may need to set the framework version in web.config. To install ASP.NET on IIS, use the [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Also, see [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) or, for ASP.NET Core, [Host on Windows with IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Resolve authentication errors if you are using only the IP address

     By default, IP addresses are assumed to be part of the Internet, and NTLM authentication is not done over the Internet. If your web site is configured in IIS to require authentication, this authentication fails. To correct this problem, you can specify the name of the remote computer instead of the IP address.
     
## <a name="other-causes"></a>Other causes

If the IIS configuration is not causing the issue, try these steps:

- Restart Visual Studio with Administrator privileges and try again.

    Some ASP.NET debugging scenarios such as using Web Deploy require elevated privileges for Visual Studio.
    
- If multiple instances of Visual Studio are running, reopen your project in one instance of Visual Studio (with Administrator privileges), and try again.

- If you are using a HOSTS file with local addresses, try using the loopback address instead of the machine's IP address.

    If you are not using local addresses, make sure your HOSTS file includes the same project URL as in your project properties, **Properties > Web > Servers** or **Properties > Debug**, depending on your project type.

## <a name="more-troubleshooting-steps"></a>More troubleshooting steps

* Bring up the localhost page in the browser on the server.

     If IIS is not installed correctly, you should get errors when you type `http://localhost` in a browser.
     
     For more information on deploying to IIS, see [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) and, for ASP.NET Core, [Host on Windows with IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Create a basic ASP.NET application on the server (or use a basic web.config file).

    If you can't get your app to work with the debugger, try creating a basic ASP.NET application locally on the server, and try to debug the basic app. (You might want to use the default ASP.NET MVC template.) If you can debug a basic app, that may help you identify what's different between the two configurations. Look for differences in settings in the web.config file, such as URL rewrite rules.

## <a name="see-also"></a>See Also  
 [Debugging Web Applications: Errors and Troubleshooting](../debugger/debugging-web-applications-errors-and-troubleshooting.md)