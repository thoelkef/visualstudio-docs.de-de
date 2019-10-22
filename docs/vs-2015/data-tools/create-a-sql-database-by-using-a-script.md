---
title: Erstellen einer SQL-Datenbank mithilfe eines Skripts | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670090"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Erstellen einer SQL-­Datenbank mithilfe eines Skripts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise verwenden Sie Visual Studio, um eine kleine Datenbank zu erstellen, die den Beispielcode für das [Erstellen einer einfachen Daten Anwendung mit ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md)enthält.

 **Inhalt**

- [Erstellen eines Skripts, das ein Datenbankschema enthält](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Erstellen eines Datenbankprojekts und Importieren eines Schemas](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Bereitstellen der Datenbank](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Um diese exemplarische Vorgehensweise abzuschließen, muss SQL Server Express localdb oder eine andere SQL-Datenbank installiert sein.

## <a name="CreateScript"></a>Erstellen eines Skripts, das ein Datenbankschema enthält

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>So erstellen Sie ein Skript, aus dem Sie ein Schema importieren können

1. Wählen Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in der Menüleiste **Datei**  > **neue**  > **Datei**aus.

     Das Dialogfeld **neue Datei** wird angezeigt.

2. Wählen Sie in der Liste **Kategorien** die Option **Allgemein**aus.

3. Wählen Sie in der Liste **Vorlagen** die Option **SQL-Datei**aus, und klicken Sie dann auf die Schaltfläche **Öffnen** .

     Der Transact-SQL-Editor wird geöffnet.

4. Kopieren Sie den folgenden Transact-SQL-Code, und fügen Sie ihn in den Transact-SQL-Editor ein.

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

5. Wählen Sie in der Menüleiste **Datei**  > **Speichern SqlQuery_1. SQL als**aus.

     Das Dialogfeld **Datei speichern** unter wird angezeigt.

6. Geben Sie im Feld **Dateiname** `SampleImportScript.sql` ein, notieren Sie den Speicherort der Datei, und klicken Sie dann auf die Schaltfläche **Speichern** .

7. Wählen Sie in der Menüleiste **Datei**  >  Projekt Mappe**Schließen**aus.

     Erstellen Sie dann ein Datenbankprojekt und importieren das Schema von dem erstellten Skript.

## <a name="CreateProject"></a>Erstellen eines Datenbankprojekts und Importieren eines Schemas

#### <a name="to-create-a-database-project"></a>So erstellen Sie ein Datenbankprojekt

1. Klicken Sie auf der Menüleiste auf **Datei** > **Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie unter **installiert**den Knoten **Vorlagen** , erweitern Sie den Knoten **andere Sprachen** , wählen Sie die Kategorie **SQL Server** aus, und wählen Sie dann die Vorlage **SQL Server Datenbankprojekt** aus.

    > [!NOTE]
    > Der Knoten **andere Sprachen** wird nicht in allen Installationen von Visual Studio angezeigt.

3. Geben Sie im Feld **Name** `Small Database` ein.

4. Aktivieren Sie das Kontrollkästchen **Projektmappenverzeichnis erstellen** , wenn es nicht bereits ausgewählt ist.

5. Deaktivieren Sie das Kontrollkästchen **zur Quell Code Verwaltung hinzufügen** , wenn es nicht bereits deaktiviert ist, und klicken Sie dann auf die Schaltfläche **OK** .

     Das Datenbankprojekt wird erstellt und in **Projektmappen-Explorer**angezeigt.

     Importieren Sie anschließend das Datenbankschema von dem Skript.

#### <a name="to-import-a-database-schema-from-a-script"></a>So importieren Sie ein Datenbankschema aus einem Skript

1. Wählen Sie in der Menüleiste **Projekt**  >   > **Skript** **importieren** aus.

2. Überprüfen Sie auf der **Willkommens** Seite den Text, und wählen Sie dann die Schaltfläche **weiter** aus.

3. Wählen Sie das Optionsfeld **einzelne Datei** aus, und klicken Sie dann auf die Schaltfläche **Durchsuchen** .

     Das Dialogfeld **SQL-Skript importieren** wird angezeigt.

4. Öffnen Sie den Ordner, in dem Sie die Datei SampleImportScript. SQL gespeichert haben, wählen Sie die Datei aus, und klicken Sie dann auf die Schaltfläche **Öffnen** .

5. Wählen Sie die Schaltfläche **Fertig** stellen, um das Dialogfeld **SQL-Skript importieren** zu schließen.

     Das Skript wird importiert, und die vom Skript definierten Objekte werden dem Datenbankprojekt hinzugefügt.

6. Überprüfen Sie die Zusammenfassung, und klicken Sie dann auf **Fertig** stellen, um das Dialogfeld **SQL-Skriptdatei importieren** zu schließen.

7. Erweitern Sie in **Projektmappen-Explorer**die Ordner "Sales", "Scripts" und "Security" des Projekts, und vergewissern Sie sich, dass Sie SQL-Dateien enthalten.

8. Überprüfen Sie in **SQL Server-Objekt-Explorer**, ob die Datenbank unter dem Knoten **Projekte** angezeigt wird.

     Jetzt enthält die Datenbank nur Systemobjekte wie Tabellen und gespeicherte Prozeduren. Nachdem Sie die Datenbank bereitgestellt haben, enthält sie die Benutzertabellen und die gespeicherten Prozeduren, die die Skripts definieren.

## <a name="DeployDatabase"></a>Bereitstellen der Datenbank
 Wenn Sie die Taste **F5** drücken, müssen Sie die Datenbank standardmäßig in einer localdb-Datenbank bereitstellen (oder veröffentlichen). Sie können die Datenbank an einem anderen Speicherort bereitstellen, indem Sie die Eigenschaften Seite für das Projekt öffnen, die Registerkarte **Debuggen** auswählen und dann die Verbindungs Zeichenfolge ändern.
