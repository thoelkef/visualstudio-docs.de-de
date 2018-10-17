---
title: 'Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren für die Northwind-Kundentabelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4972c1341490f78bba03bdd390ac13903c55be84
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204047"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Exemplarische Vorgehensweise: Erstellen von aktualisierten gespeicherten Prozeduren für die Northwind-Kundentabelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einige Hilfethemen in der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Dokumentation erfordern weitere gespeicherte Prozeduren in der Northwind-Beispieldatenbank, zum Ausführen von Aktualisierungen (Einfügungen, Updates und Löschungen) von Daten in der Customers-Tabelle.  
  
 Diese exemplarische Vorgehensweise enthält eine Anleitung für das Erstellen dieser zusätzlichen gespeicherten Prozeduren in der Beispieldatenbank Northwind für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Der Abschnitt "Weitere Schritte" später in diesem Thema enthält Links, die zeigen, wie Sie mit diesen zusätzlichen gespeicherten Prozeduren arbeiten.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die folgenden Aufgaben ausführen:  
  
-   Erstellen einer Verbindung mit der Beispieldatenbank Northwind.  
  
-   Erstellen neuer gespeicherter Prozeduren.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:  
  
-   Zugriff auf die SQL Server-Version der Beispieldatenbank Northwind. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Verbinden mit der Datenbank Northwind  
 Diese exemplarische Vorgehensweise erfordert eine Verbindung zur SQL Server-Version der Northwind-Datenbank. Das folgende Verfahren enthält Anweisungen für das Erstellen der Datenverbindung.  
  
> [!NOTE]
>  Wenn Sie bereits eine Datenverbindung zur Northwind-Datenbank haben, können Sie mit dem nächsten Abschnitt fortfahren: Erstellen der gespeicherten Prozeduren.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>So erstellen Sie eine Datenverbindung zur Northwind-SQL Server-Datenbank  
  
1.  Auf der **Ansicht** Menü klicken Sie auf **Server-Explorer**/**Datenbank-Explorer**.  
  
2.  Mit der rechten Maustaste **Datenverbindungen** , und klicken Sie auf **Verbindung hinzufügen**.  
  
3.  In der **Datenquelle auswählen** Dialogfeld klicken Sie auf **Microsoft SQL Server**, und klicken Sie dann auf **OK**.  
  
     Wenn die **Verbindung hinzufügen** Dialogfeld geöffnet wird, und die **Datenquelle** ist nicht **Microsoft SQL Server (SqlClient)**, klicken Sie auf **ändern** zum Öffnen der **Datenquelle auswählen/wechseln** Dialogfeld klicken Sie auf **Microsoft SQL Server**, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie auf eine **Servernamen** in der Dropdownliste aus, oder geben Sie den Namen des Servers, auf dem die Northwind-Datenbank gespeichert ist.  
  
5.  Basierend auf den Anforderungen der Datenbank oder der Anwendung, klicken Sie entweder auf **Windows-Authentifizierung verwenden** oder verwenden Sie einen bestimmten Benutzernamen und ein Kennwort zum Anmelden bei des Computers mit SQL Server (**fürSQLServer-Authentifizierung**).  
  
6.  Klicken Sie auf der Northwind-Datenbank in der **auswählen oder Eingeben eines Datenbanknamens** Liste.  
  
7.  Klicken Sie auf **OK**.  
  
     Die Datenverbindung wurde **Server-Explorer**/**Datenbank-Explorer**.  
  
## <a name="creating-the-stored-procedures"></a>Erstellen der gespeicherte Prozeduren  
 Erstellen Sie die gespeicherten Prozeduren, durch Ausführen des bereitgestellten SQL-Skripts für die Northwind-Datenbank mithilfe der [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) in verfügbaren **Server-Explorer** /  **Datenbank-Explorer**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>So erstellen Sie gespeicherte Prozeduren mithilfe eines SQL-Skripts  
  
1.  Erweitern Sie die Northwind-Datenbank in **Server-Explorer**/**Datenbank-Explorer**.  
  
2.  Mit der rechten Maustaste die **gespeicherte Prozeduren** Knoten, und klicken Sie auf **neue gespeicherte Prozedur hinzufügen**.  
  
3.  Fügen Sie den folgenden Code in den Code-Editor ein, sodass die `CREATE PROCEDURE`-Vorlage ersetzt wird:  
  
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
  
4.  Markiert den gesamten Text im Code-Editor, mit der rechten Maustaste in des ausgewählten Texts, und klicken Sie auf **Auswahl ausführen**.  
  
     Die gespeicherten Prozeduren SelectCustomers, InsertCustomers, UpdateCustomers und DeleteCustomers werden für die Datenbank Northwind erstellt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem Sie jetzt die gespeicherten Prozeduren erstellt haben, versuchen Sie die folgenden exemplarischen Vorgehensweisen, in denen demonstriert wird, wie Sie damit arbeiten:  
  
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)