---
title: "Exemplarische Vorgehensweise: Erstellen einer kleinen Beispieldatenbank | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen einer kleinen Beispieldatenbank
In dieser exemplarischen Vorgehensweise verwenden Sie Visual Studio, um eine kleine Datenbank zu erstellen, die den Beispielcode für [Exemplarische Vorgehensweise: Erstellen einer einfachen Datenanwendung mit ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md) enthält.  
  
 **In diesem Thema**  
  
-   [Erstellen eines Skripts mit einem Datenbankschema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Erstellen eines Datenbankprojekts und Importieren eines Schemas](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Bereitstellen der Datenbank](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise abzuschließen, muss [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] installiert sein.  Ferner müssen Sie eine Verbindung mit einem Datenbankserver oder einer LocalDB\-Datenbank herstellen können, auf dem bzw. für die Sie über Berechtigungen zum Erstellen und Bereitstellen einer Datenbank verfügen.  
  
##  <a name="CreateScript"></a> Erstellen eines Skripts mit einem Datenbankschema  
  
#### So erstellen Sie ein Skript, aus dem Sie ein Schema importieren können  
  
1.  Wählen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der Menüleiste die Optionen **Datei**, **Neu** und **Datei**.  
  
     Das Dialogfeld **Neue Datei** wird angezeigt.  
  
2.  Wählen Sie in der Liste **Kategorien** den Eintrag **Allgemein** aus.  
  
3.  In der Liste **Vorlagen** wählen Sie **SQL\-Datei** aus und klicken dann auf die Schaltfläche **Öffnen**.  
  
     Der Transact\-SQL\-Editor wird geöffnet.  
  
4.  Kopieren Sie den Transact\-SQL\-Code, und fügen Sie ihn im Transact\-SQL\-Editor ein.  
  
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
  
5.  Klicken Sie in der Menüleiste **Datei** auf **SqlQuery\_1.sql speichern unter**.  
  
     Das Dialogfeld **Datei speichern unter** wird angezeigt.  
  
6.  Geben Sie im Feld **Dateiname**`SampleImportScript.sql` ein, merken Sie sich den Speicherort der Datei, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
7.  Wählen Sie in der Menüleiste **Datei**, **Projektmappe schließen** aus.  
  
     Erstellen Sie dann ein Datenbankprojekt und importieren das Schema von dem erstellten Skript.  
  
##  <a name="CreateProject"></a> Erstellen eines Datenbankprojekts und Importieren eines Schemas  
  
#### So erstellen Sie ein Datenbankprojekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Erweitern Sie unter **Installiert** den Knoten **Vorlagen**, erweitern Sie den Knoten **Andere Sprachen**, wählen Sie die Kategorie **SQL Server** aus, und wählen Sie dann die Vorlage **SQL Server\-Datenbankprojekt** aus.  
  
    > [!NOTE]
    >  Der Knoten **Andere Sprachen** wird nicht in allen Installationen von Visual Studio angezeigt.  
  
3.  Geben Sie im Feld **Name** den Namen `Small Database` ein.  
  
4.  Aktivieren Sie ggf. das Kontrollkästchen **Projektmappenverzeichnis erstellen**.  
  
5.  Deaktivieren Sie ggf. das Kontrollkästchen **Zur Quellcodeverwaltung hinzufügen**, und klicken Sie dann auf **OK**.  
  
     Das Datenbankprojekt wird erstellt und im **Projektmappen\-Explorer** angezeigt.  
  
     Importieren Sie anschließend das Datenbankschema von dem Skript.  
  
#### So importieren Sie ein Datenbankschema aus einem Skript  
  
1.  Wählen Sie in der Menüleiste **Projekt**, **Importieren**, **Skript** aus.  
  
2.  Überprüfen Sie den Text auf der Startseite, und klicken Sie dann auf die Schaltfläche **Weiter**.  
  
3.  Wählen Sie das Optionsfeld **Einzelne Datei** aus, und klicken Sie dann auf die Schaltfläche **Durchsuchen**.  
  
     Das Dialogfeld **SQL\-Skript importieren** wird angezeigt.  
  
4.  Öffnen Sie den Ordner, in dem Sie die Datei "SampleImportScript.sql" gespeichert haben, wählen Sie sie aus, und klicken Sie dann auf die Schaltfläche **Öffnen**.  
  
5.  Klicken Sie auf die Schaltfläche **Fertig stellen**, um das Dialogfeld **SQL\-Skript importieren** zu schließen.  
  
     Das Skript wird importiert, und die vom Skript definierten Objekte werden dem Datenbankprojekt hinzugefügt.  
  
6.  Überprüfen Sie die Zusammenfassung, und klicken Sie dann auf die Schaltfläche **Fertig stellen**, um das Dialogfeld **SQL\-Skriptdatei importieren** zu schließen.  
  
7.  Erweitern Sie im **Projektmappen\-Explorer** die Vertriebs\-, Skript\- und Sicherheitsordner Ihres Projekts, und stellen Sie sicher, dass sie SQL\-Dateien enthalten.  
  
8.  Überprüfen Sie im **SQL Server\-Objekt\-Explorer**, ob die Datenbank im Knoten **Projekte** angezeigt wird.  
  
     Jetzt enthält die Datenbank nur Systemobjekte wie Tabellen und gespeicherte Prozeduren.  Nachdem Sie die Datenbank bereitgestellt haben, enthält sie die Benutzertabellen und die gespeicherten Prozeduren, die die Skripts definieren.  
  
##  <a name="DeployDatabase"></a> Bereitstellen der Datenbank  
 Wenn Sie die Taste F5 drücken, stellen Sie die Datenbank standardmäßig in einer LocalDB\-Datenbank bereit bzw. veröffentlichen sie.  Sie können die Datenbank an einem anderen Speicherort bereitstellen, indem Sie die Eigenschaftenseite für das Projekt öffnen, die Registerkarte **Debuggen** auswählen und dann die Verbindungszeichenfolge ändern.