---
title: Erstellen Sie eine SQL­Datenbank mithilfe eines Skripts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd0bf5c0e95b4c859dc2d6470ab6f922041b20ba
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049879"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Erstellen Sie eine SQL­Datenbank mithilfe eines Skripts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise verwenden Sie Visual Studio eine kleine Datenbank zu erstellen, enthält den Beispielcode für [erstellen eine einfachen datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Inhalt**  
  
- [Erstellen Sie ein Skript, das ein Datenbankschema enthält](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
- [Erstellen eines Datenbankprojekts und Importieren eines Schemas](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
- [Bereitstellen der Datenbank](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Abschließen dieser exemplarischen Vorgehensweise muss SQL Server Express LocalDB oder einer anderen SQL-Datenbank installiert sein.  
  
## <a name="CreateScript"></a> Erstellen Sie ein Skript, das ein Datenbankschema enthält  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>So erstellen Sie ein Skript, aus dem Sie ein Schema importieren können  
  
1. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], wählen Sie auf der Menüleiste **Datei** > **neu** > **Datei**.  
  
     Die **neue Datei** Dialogfeld wird angezeigt.  
  
2. In der **Kategorien** Liste **allgemeine**.  
  
3. In der **Vorlagen** Liste **Sql-Datei**, und wählen Sie dann die **öffnen** Schaltfläche.  
  
     Die Transact-SQL-Editor wird geöffnet.  
  
4. Kopieren Sie den folgenden Transact-SQL-Code, und fügen Sie ihn in den Transact-SQL-Editor.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5. Wählen Sie auf der Menüleiste **Datei** > **Sqlquery_1.SQL speichern**.  
  
     Die **Datei speichern unter** Dialogfeld wird angezeigt.  
  
6. In der **Dateiname** geben `SampleImportScript.sql`, notieren Sie den Speicherort, in dem Sie die Datei speichern, und wählen Sie dann, die **speichern** Schaltfläche.  
  
7. Wählen Sie auf der Menüleiste **Datei** > **Projektmappe schließen**.  
  
     Erstellen Sie dann ein Datenbankprojekt und importieren das Schema von dem erstellten Skript.  
  
## <a name="CreateProject"></a> Erstellen eines Datenbankprojekts und Importieren eines Schemas  
  
#### <a name="to-create-a-database-project"></a>So erstellen Sie ein Datenbankprojekt  
  
1. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2. Unter **installiert**, erweitern Sie die **Vorlagen** Knoten, erweitern Sie die **andere Sprachen** Knoten die **SQL Server** (Kategorie), und klicken Sie dann Wählen Sie die **SQL Server-Datenbankprojekt** Vorlage.  
  
    > [!NOTE]
    >  Die **andere Sprachen** Knoten nicht in allen Installationen von Visual Studio angezeigt.  
  
3. In der **Namen** geben `Small Database`.  
  
4. Wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen, wenn sie nicht bereits ausgewählt ist.  
  
5. Deaktivieren der **zur quellcodeverwaltung hinzufügen** das Kontrollkästchen, falls er noch nicht gelöscht, und wählen Sie dann die **OK** Schaltfläche.  
  
     Das Datenbankprojekt wird erstellt und wird im **Projektmappen-Explorer**.  
  
     Importieren Sie anschließend das Datenbankschema von dem Skript.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>So importieren Sie ein Datenbankschema aus einem Skript  
  
1. Wählen Sie auf der Menüleiste **Projekt** > **Import** > **Skript**.  
  
2. Auf der **Willkommen** Seite überprüfen Sie den Text, und wählen Sie dann die **Weiter** Schaltfläche.  
  
3. Wählen Sie die **Einzeldatei** Optionsfeld aus, und wählen Sie dann die **Durchsuchen** Schaltfläche.  
  
     Die **SQL-Skript importieren** Dialogfeld wird angezeigt.  
  
4. Öffnen Sie den Ordner, in dem Sie die Datei SampleImportScript.sql gespeichert haben, wählen Sie die Datei, und wählen Sie dann die **öffnen** Schaltfläche.  
  
5. Wählen Sie die **Fertig stellen** Schaltfläche zum Schließen der **SQL-Skript importieren** Dialogfeld.  
  
     Das Skript wird importiert, und die vom Skript definierten Objekte werden dem Datenbankprojekt hinzugefügt.  
  
6. Überprüfen Sie die Zusammenfassung, und klicken Sie dann auf die **Fertig stellen** Schaltfläche zum Schließen der **SQL-Skriptdatei importieren** Dialogfeld.  
  
7. In **Projektmappen-Explorer**, erweitern Sie den Vertrieb, Skript- und Sicherheitsordner Ihres Projekts, und stellen Sie sicher, dass sie SQL-Dateien enthalten.  
  
8. In **Objekt-Explorer von SQL Server**, stellen Sie sicher, dass die Datenbank wird, unter angezeigt dem **Projekte** Knoten.  
  
     Jetzt enthält die Datenbank nur Systemobjekte wie Tabellen und gespeicherte Prozeduren. Nachdem Sie die Datenbank bereitgestellt haben, enthält sie die Benutzertabellen und die gespeicherten Prozeduren, die die Skripts definieren.  
  
## <a name="DeployDatabase"></a> Bereitstellen der Datenbank  
 Beim Drücken der **F5** Schlüssel, Sie zu einer LocalDB-Datenbank wird standardmäßig die Datenbank bereitstellen (oder veröffentlichen). Sie können die Datenbank an einen anderen Speicherort bereitstellen, durch Öffnen der Eigenschaftenseite für das Projekt auswählen der **Debuggen** Registerkarte, und klicken Sie dann die Verbindungszeichenfolge ändern.
