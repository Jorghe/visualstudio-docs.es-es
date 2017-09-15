---
title: 'How to: Save data by using a transaction | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
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
ms.sourcegitcommit: f4b17810a2f59aeee8d6002059d65928882fd51f
ms.openlocfilehash: d68efadb84b5c0cdecea1d606618da808ea0fa1a
ms.contentlocale: es-es
ms.lasthandoff: 09/08/2017

---
# <a name="how-to-save-data-by-using-a-transaction"></a>How to: Save data by using a transaction
You save data in a transaction by using the <xref:System.Transactions> namespace. Use the <xref:System.Transactions.TransactionScope> object to participate in a transaction that is automatically managed for you.  
  
 Projects are not created with a reference to the System.Transactions assembly, so you need to manually add a reference to projects that use transactions.  
  
 The easiest way to implement a transaction is to instantiate a <xref:System.Transactions.TransactionScope> object in a `using` statement. (For more information, see [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement), and [using Statement](/dotnet/csharp/language-reference/keywords/using-statement).) The code that runs within the `using` statement participates in the transaction.  
  
 To commit the transaction, call the <xref:System.Transactions.TransactionScope.Complete%2A> method as the last statement in the using block.  
  
 To roll back the transaction, throw an exception prior to calling the <xref:System.Transactions.TransactionScope.Complete%2A> method.  
  
### <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>To add a reference to the System.Transactions.dll  
  
1.  On the **Project** menu, select **Add Reference**.  
  
2.  On the **.NET** tab (**SQL Server** tab for SQL Server projects), select **System.Transactions**, and then select **OK**.  
  
     A reference to System.Transactions.dll is added to the project.  
  
### <a name="to-save-data-in-a-transaction"></a>To save data in a transaction  
  
-   Add code to save data within the using statement that contains the transaction. The following code shows how to create and instantiate a <xref:System.Transactions.TransactionScope> object in a using statement:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]  [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>See Also  
 [Save data back to the database](../data-tools/save-data-back-to-the-database.md)  
 [Walkthrough: Save data in a transaction](../data-tools/save-data-in-a-transaction.md)  