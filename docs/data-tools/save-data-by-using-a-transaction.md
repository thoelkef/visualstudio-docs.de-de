---
title: "Gewusst wie: Speichern von Daten mithilfe von Transaktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Speichern"
  - "Speichern von Daten, Verwenden von Transaktionen"
  - "System.Transactions-Namespace"
  - "Transaktionen, Speichern von Daten"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Speichern von Daten mithilfe von Transaktionen
Sie können Daten im Rahmen einer Transaktion speichern, indem Sie den <xref:System.Transactions>\-Namespace verwenden.  Mit dem <xref:System.Transactions.TransactionScope>\-Objekt können Sie an einer Transaktion teilnehmen, die automatisch verwaltet wird.  
  
 Projekte erhalten bei ihrer Erstellung keinem Verweis auf die System.Transactions\-Assembly. Für Projekte, die Transaktionen verwenden, müssen Sie manuell einen Verweis hinzufügen.  
  
> [!NOTE]
>  Der <xref:System.Transactions>\-Namespace wird ab Windows 2000 unterstützt.  
  
 Der einfachste Weg, Transaktionen zu implementieren, besteht darin, in einer `using`\-Anweisung ein <xref:System.Transactions.TransactionScope>\-Objekt zu instanziieren.  Weitere Informationen finden Sie unter [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) und [using\-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement). Der innerhalb der `using`\-Anweisung ausgeführte Code nimmt an der Transaktion teil.  
  
 Um einen Commit für eine Transaktion durchzuführen, rufen Sie als letzte Anweisung im using\-Block die <xref:System.Transactions.TransactionScope.Complete%2A>\-Methode auf.  
  
 Um einen Rollback für die Transaktion durchzuführen, lösen Sie vor dem Aufrufen der <xref:System.Transactions.TransactionScope.Complete%2A>\-Methode eine Ausnahme aus.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion](../data-tools/save-data-in-a-transaction.md).  
  
### So fügen Sie einen Verweis auf die System.Transactions\-DLL hinzu  
  
1.  Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus.  
  
2.  Wählen Sie auf der Registerkarte **.NET** \(für SQL Server\-Projekte: Registerkarte **SQL Server**\) die Option **System.Transactions** aus, und klicken Sie auf **OK**.  
  
     Dem Projekt wird ein Verweis auf System.Transactions.dll hinzugefügt.  
  
### So speichern Sie Daten im Rahmen einer Transaktion  
  
-   Fügen Sie Code hinzu, um Daten innerhalb der using\-Anweisung zu speichern, die die Transaktion enthält.  Der folgende Code zeigt, wie ein <xref:System.Transactions.TransactionScope>\-Objekt in einer using\-Anweisung erstellt und instanziiert wird:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion](../data-tools/save-data-in-a-transaction.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)