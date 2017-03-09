---
title: "Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren f&#252;r die Northwind-Kundentabelle | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Northwind-Beispieldatenbank"
  - "O/R-Designer, Gespeicherte Prozeduren"
  - "Gespeicherte Prozeduren [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren f&#252;r die Northwind-Kundentabelle
Einige Hilfethemen in der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Dokumentation erfordern weitere gespeicherte Prozeduren in der Beispieldatenbank Northwind für das Durchführen von Aktualisierungen \(Einfügungen, Aktualisierung und Löschungen\) von Daten in der Tabelle Customers.  
  
 Diese exemplarische Vorgehensweise enthält eine Anleitung für das Erstellen dieser zusätzlichen gespeicherten Prozeduren in der Beispieldatenbank Northwind für [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 Der Abschnitt "Weitere Schritte" später in diesem Thema enthält Links, die zeigen, wie Sie mit diesen zusätzlichen gespeicherten Prozeduren arbeiten.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:  
  
-   Erstellen einer Verbindung mit der Beispieldatenbank Northwind.  
  
-   Erstellen neuer gespeicherter Prozeduren.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:  
  
-   Zugriff auf die SQL Server\-Version der Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Verbinden mit der Datenbank Northwind  
 Diese exemplarische Vorgehensweise erfordert eine Verbindung zur SQL Server\-Version der Northwind\-Datenbank.  Das folgende Verfahren enthält Anweisungen für das Erstellen der Datenverbindung.  
  
> [!NOTE]
>  Wenn Sie bereits eine Datenverbindung zur Northwind\-Datenbank haben, können Sie mit dem nächsten Abschnitt fortfahren: Erstellen der gespeicherten Prozeduren.  
  
#### So erstellen Sie eine Datenverbindung zur Northwind\-SQL Server\-Datenbank  
  
1.  Klicken Sie im Menü **Ansicht** auf **Server\-Explorer** oder **Datenbank\-Explorer**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenverbindungen** und dann auf **Verbindung hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld **Datenquelle auswählen** auf **Microsoft SQL Server** und dann auf **OK**.  
  
     Wenn sich das Dialogfeld **Datenquelle auswählen** öffnet und die **Datenquelle** nicht **Microsoft SQL Server \(SqlClient\)** ist, klicken Sie auf **Ändern**, sodass das Dialogfeld **Datenquelle auswählen\/ändern** geöffnet wird. Klicken Sie nun **Microsoft SQL Server** und anschließend **OK**.  
  
4.  Klicken Sie auf einen **Servernamen** in der Dropdownliste oder geben Sie den Namen des Servers ein, auf dem sich die Northwind\-Datenbank befindet.  
  
5.  Abhängig von den Anforderungen der Datenbank oder Anwendung klicken entweder auf **Windows\-Authentifizierung verwenden** oder nutzen Sie einen spezifischen Benutzernamen und ein Kennwort, um sich am Computer anzumelden, auf dem SQL Server läuft \(**SQL Server\-Authentifizierung**\).  
  
6.  Klicken Sie die Northwind\-Datenbank in der Liste **Datenbankname auswählen oder eingeben**.  
  
7.  Klicken Sie auf **OK**.  
  
     Die Datenverbindung wird **Server\-Explorer**\/**Datenbank\-Explorer** hinzugefügt.  
  
## Erstellen der gespeicherte Prozeduren  
 Erstellen Sie die gespeicherten Prozeduren, indem Sie das bereitgestellte SQL\-Skript auf die Northwind\-Datenbank mithilfe des [Visual Database Tools](http://msdn.microsoft.com/de-de/6b145922-2f00-47db-befc-bf351b4809a1) anwenden, das in **Server\-Explorer**\/**Datenbank\-Explorer** verfügbar ist.  
  
#### So erstellen Sie gespeicherte Prozeduren mithilfe eines SQL\-Skripts  
  
1.  Erweitern Sie die Northwind\-Datenbank in **Server\-Explorer**\/**Datenbank\-Explorer**.  
  
2.  Klicken Sie mit der rechten Maustaste den Knoten **Gespeicherte Prozedur** und klicken Sie anschließend auf **Neue gespeicherte Prozedur hinzufügen**.  
  
3.  Fügen Sie den folgenden Code in den Code\-Editor ein, sodass die `CREATE PROCEDURE`\-Vorlage ersetzt wird:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Wählen Sie den gesamten Text im Code\-Editor aus, klicken Sie diesen anschließend mit der rechten Maustaste an und klicken Sie nun auf **Auswahl ausführen**.  
  
     Die gespeicherten Prozeduren SelectCustomers, InsertCustomers, UpdateCustomers und DeleteCustomers werden für die Datenbank Northwind erstellt.  
  
## Nächste Schritte  
 Nachdem Sie jetzt die gespeicherten Prozeduren erstellt haben, versuchen Sie die folgenden exemplarischen Vorgehensweisen, in denen demonstriert wird, wie Sie damit arbeiten:  
  
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Exemplarische Vorgehensweise: Anpassen des Einfüge\-, Update\- und Löschverhaltens von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)