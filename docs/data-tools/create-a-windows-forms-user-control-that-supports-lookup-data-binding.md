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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6cc105d20ea3a1faf09fd75bcbf9e38cd5fdc833
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924559"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das Bindung an Nachschlagedaten unterstützt
Anzeigen von Daten in Windows Forms können Sie vorhandenen Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung die Funktionalität ist in den Standardsteuerelementen nicht verfügbar. erfordert. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementieren, können drei Eigenschaften enthalten, die an Daten gebunden werden können. Solche Steuerelemente ähneln einem <xref:System.Windows.Forms.ComboBox>-Steuerelement.

 Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelemente zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung Attributverwendung|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, wie das <xref:System.Windows.Forms.ComboBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|

 In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement erstellt, das an Daten aus zwei Tabellen gebunden ist. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet. Das Nachschlagesteuerelement gebunden ist, um die `CustomerID` aus der `Orders` Tabelle. Dieser Wert wird verwendet, zum Nachschlagen der `CompanyName` aus der `Customers` Tabelle.

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

-   Erstellen Sie ein neues **Windows Forms-Anwendung**.

-   Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.

-   Entwerfen des Benutzersteuerelements im visuellen Designer.

-   Implementieren des `LookupBindingProperty`-Attributs.

-   Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.

-   Festlegen der **"CustomerID"** Spalte auf der **Bestellungen** -Tabelle in der **Datenquellen** Fenster, um das neue Steuerelement verwendet.

-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.

## <a name="prerequisites"></a>Vorraussetzungen

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **LookupControlWalkthrough**, und wählen Sie dann **OK**.

     Die **LookupControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement
 In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement aus erstellt eine **Benutzersteuerelement**, fügen Sie also eine **Benutzersteuerelement** Element für die **LookupControlWalkthrough** Projekt.

#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu

1.  Von der **Projekt** , wählen Sie im Menü **Benutzersteuerelement hinzufügen**.

2.  Typ `LookupBox` in die **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.

     Die **LookupBox** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.

## <a name="design-the-lookupbox-control"></a>Entwerfen des LookupBox-Steuerelements

#### <a name="to-design-the-lookupbox-control"></a>So entwerfen Sie das LookupBox-Steuerelement

-   Ziehen Sie eine <xref:System.Windows.Forms.ComboBox> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.

## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu
 Implementieren Sie für Nachschlagesteuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>So implementieren Sie das LookupBindingProperties-Attribut

1.  Wechseln der **LookupBox** -Steuerelement zur Codeansicht. (Auf der **Ansicht** Menü wählen **Code**.)

2.  Ersetzen Sie den Code in `LookupBox` durch folgenden Code:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank
Dieser Schritt wird erstellt, mit einer Datenquelle mithilfe der **Datenquellenkonfiguration** Assistenten, auf der Grundlage der `Customers` und `Orders` Tabellen in der Beispieldatenbank Northwind.

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.

5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Customers` und `Orders` Tabellen, und klicken Sie dann auf **Fertig stellen**.

     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die `Customers` und `Orders` Tabellen angezeigt werden, der **Datenquellen** Fenster.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Legen Sie die CustomerID-Spalte der Tabelle Orders, verwenden Sie das LookupBox-Steuerelement
 In der **Datenquellen** Fenster können Sie das Steuerelement erstellt werden, vor dem Ziehen von Elementen auf das Formular festlegen.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>So legen Sie die Bindung der Spalte "CustomerID" an das LookupBox-Steuerelement fest

1.  Open **Form1** im Designer.

2.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.

3.  Erweitern Sie die **Bestellungen** Knoten (in der **Kunden** Knoten unten die **Fax** Spalte).

4.  Klicken Sie auf die Dropdown-Pfeil der **Bestellungen** Knoten, und wählen Sie **Details** aus der Steuerungsliste.

5.  Klicken Sie auf die Dropdown-Pfeil der **"CustomerID"** Spalte (in der **Bestellungen** Knoten), und wählen Sie **anpassen**.

6.  Wählen Sie die **LookupBox** aus der Liste der **zugeordnete Steuerelemente** in die **Optionen für die Anpassung** Dialogfeld.

7.  Klicken Sie auf **OK**.

8.  Klicken Sie auf die Dropdown-Pfeil der **"CustomerID"** Spalte, und wählen Sie **LookupBox**.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows Form

-   Ziehen Sie die **Bestellungen** Knoten aus der **Datenquellen** auf das Windows-Formular, und überprüfen Sie, ob die **LookupBox** Steuerelement wird verwendet, um die Anzeige der Daten in die `CustomerID` die Spalte.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Binden des Steuerelements zum Nachschlagen von CompanyName in der Customers-Tabelle

#### <a name="to-setup-the-lookup-bindings"></a>So richten Sie die Nachschlagebindungen ein

-   Wählen Sie im **Kunden** Knoten in der **Datenquellen** angezeigt, und ziehen Sie es auf das Kombinationsfeld für den Sie im Dialogfeld die **CustomerIDLookupBox** auf **Form1** .

     Hiermit wird die Datenbindung zum Anzeigen der `CompanyName` aus der `Customers` Tabelle, und gleichzeitig die `CustomerID` Wert aus der `Orders` Tabelle.

## <a name="running-the-application"></a>Ausführen der Anwendung

#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

-   Drücken Sie **F5**, um die Anwendung auszuführen.

-   Navigieren Sie durch einige Datensätze aus, und überprüfen Sie, ob die `CompanyName` wird in der `LookupBox` Steuerelement.

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)