---
title: 'Vorgehensweise: Speichern von Daten mithilfe von Transaktionen | Microsoft Docs'
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
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 23cf5ee9ef7369d8c0f52adde639adad4abe3ae6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Vorgehensweise: Speichern von Daten mithilfe von Transaktionen
Speichern von Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. Verwenden der <xref:System.Transactions.TransactionScope> Objekt, das in einer Transaktion teilnehmen, die automatisch für Sie verwaltet wird.  
  
Projekte werden nicht mit einem Verweis auf die System.Transactions-Assembly erstellt, daher müssen Sie manuell einen Verweis zu Projekten hinzufügen, die Transaktionen verwenden.  
  
Die einfachste Möglichkeit zum Implementieren einer Transaktions wird beim Instanziieren einer <xref:System.Transactions.TransactionScope> -Objekt in ein `using` Anweisung. (Weitere Informationen finden Sie unter [Using-Anweisung](/dotnet/visual-basic/language-reference/statements/using-statement), und [mit Anweisung](/dotnet/csharp/language-reference/keywords/using-statement).) Die in geschriebener Code die `using` Anweisung in der Transaktion beteiligt ist.  
  
Um die Transaktion einen Commit auszuführen, rufen Sie die <xref:System.Transactions.TransactionScope.Complete%2A> als die letzte Anweisung in der Methode zu blockieren.  
  
Um ein Rollback die Transaktion, eine Ausnahme vor dem Aufruf der <xref:System.Transactions.TransactionScope.Complete%2A> Methode.  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>So fügen Sie einen Verweis auf die "System.Transactions.dll" hinzu  
  
1.  Auf der **Projekt** klicken Sie im Menü **Verweis hinzufügen**.  
  
2.  Auf der **.NET** Registerkarte (**SQL Server** Registerkarte für SQL Server-Projekte), wählen **System.Transactions**, und wählen Sie dann **OK**.  
  
     Ein Verweis auf "System.Transactions.dll" wird dem Projekt hinzugefügt.  
  
## <a name="to-save-data-in-a-transaction"></a>Zum Speichern von Daten in einer Transaktion  
  
-   Fügen Sie Code zum Speichern von Daten innerhalb der using-Anweisung, die Transaktion enthält. Der folgende Code zeigt das Erstellen und Instanziieren einer <xref:System.Transactions.TransactionScope> Objekt in einer mit Anweisung:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>Siehe auch
[Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)  
[Exemplarische Vorgehensweise: Speichern von Daten in einer Transaktion](../data-tools/save-data-in-a-transaction.md)  