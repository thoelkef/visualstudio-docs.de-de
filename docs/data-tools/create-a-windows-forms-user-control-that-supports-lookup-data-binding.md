---
title: Verwendung von Nachschlagetabellen in der Datenbindung - Windows Forms-Steuerelemente | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: bcdfb4640e88289b02f2f8813c39b66eaad3827d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889422"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das Nachschlagedatenbindung unterstützt

Zum Anzeigen von Daten in Windows Forms können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementieren, können drei Eigenschaften enthalten, die an Daten gebunden werden können. Solche Steuerelemente ähneln einem <xref:System.Windows.Forms.ComboBox>-Steuerelement.

Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelemente zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung Attributverwendung|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, wie das <xref:System.Windows.Forms.ComboBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|

In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement erstellt, das an Daten aus zwei Tabellen gebunden ist. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet. Das Nachschlagesteuerelement gebunden ist, um die `CustomerID` aus der `Orders` Tabelle. Dieser Wert wird verwendet, zum Nachschlagen der `CompanyName` aus der `Customers` Tabelle.

Im Verlauf dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie:

-   Erstellen Sie eine neue **Windows Forms-Anwendung**.

-   Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.

-   Entwerfen des Benutzersteuerelements im visuellen Designer.

-   Implementieren des `LookupBindingProperty`-Attributs.

-   Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.

-   Die Spalte **CustomerID** in der Tabelle **Orders** im **Datenquellenfenster** festlegen, um das neue Steuerelement zu verwenden.

-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-app-project"></a>Erstellen Sie ein Windows Forms-app-Projekt

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung** Projekt.

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **LookupControlWalkthrough**, und wählen Sie dann **OK**.

     Das Projekt **LookupControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt

In dieser exemplarischen Vorgehensweise wird aus einem **Benutzersteuerelement** ein Nachschlagesteuerelement erstellt. Fügen Sie dem Projekt **LookupControlWalkthrough** zunächst also ein **Benutzersteuerelement** hinzu.

1.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

2.  Typ `LookupBox` in die **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.

     Das **LookupBox**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.

## <a name="design-the-lookupbox-control"></a>Entwerfen des LookupBox-Steuerelements

Um das LookupBox-Steuerelement zu entwerfen, ziehen Sie eine <xref:System.Windows.Forms.ComboBox> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.

## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu

Implementieren Sie für Nachschlagesteuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Wechseln Sie für das **LookupBox**-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.)

2.  Ersetzen Sie den Code in `LookupBox` durch folgenden Code:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank

In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle erstellt, die auf den Tabellen `Customers` und `Orders` der Beispieldatenbank Northwind basiert.

1.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    -   Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8.  Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig stellen**.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im **Datenquellenfenster** angezeigt.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Legen Sie die CustomerID-Spalte der Tabelle Orders, verwenden Sie das LookupBox-Steuerelement

Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.

1.  Öffnen Sie **Form1** im Designer.

2.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.

3.  Erweitern Sie den Knoten **Orders** (denjenigen, der sich im Knoten **Customers** unterhalb der Spalte **Fax** befindet).

4.  Klicken Sie im Knoten **Orders** auf den Dropdownpfeil, und wählen Sie in der Steuerelementliste die Option **Details** aus.

5.  Klicken Sie in der Spalte **CustomerID** (im Knoten **Orders**) auf den Dropdownpfeil, und wählen Sie **Anpassen** aus.

6.  Wählen Sie im Dialogfeld **Data UI Customization Options** (Optionen für die Anpassung der Datenbenutzeroberfläche) in der Liste **Zugeordnete Steuerelemente** den Eintrag **LookupBox** aus.

7.  Klicken Sie auf **OK**.

8.  Klicken Sie in der Spalte **CustomerID** auf den Dropdownpfeil, und wählen Sie **LookupBox** aus.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zu dem Formular

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf **Form1** ziehen.

Ziehen Sie zum Erstellen von datengebundenen Steuerelementen auf dem Windows-Formular die **Bestellungen** Knoten aus der **Datenquellen** auf das Windows-Formular, und überprüfen Sie, ob der **LookupBox** Steuerelement ist zum Anzeigen der Daten in die `CustomerID` Spalte.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Binden des Steuerelements zum Nachschlagen von CompanyName in der Customers-Tabelle

Um die nachschlagebindungen einzurichten, wählen Sie im **Kunden** Knoten in der **Datenquellen** angezeigt, und ziehen Sie es auf das Kombinationsfeld für den Sie im Dialogfeld die **CustomerIDLookupBox** auf **Form1**.

Damit wird die Datenbindung so eingerichtet, dass der Wert für `CompanyName` aus der Tabelle `Customers` angezeigt und gleichzeitig der Wert für `CustomerID` aus der Tabelle `Orders` beibehalten wird.

## <a name="run-the-application"></a>Ausführen der Anwendung

-   Drücken Sie **F5**, um die Anwendung auszuführen.

-   Navigieren Sie durch einige Datensätze, und prüfen Sie, ob im `LookupBox`-Steuerelement der Wert von `CompanyName` angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)