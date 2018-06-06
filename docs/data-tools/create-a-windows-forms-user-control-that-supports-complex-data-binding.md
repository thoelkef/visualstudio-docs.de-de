---
title: Erstellen Sie ein Windows Forms-Benutzersteuerelement mit der Datenbindung
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e48e6a3a5694a518f30b3d9ec749d01b1e7127b8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746503"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt

Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandene Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.

Weitere Informationen zu Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Beim Erstellen von Steuerelementen für die Verwendung in Datenbindungsszenarien müssen Sie eine der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung-Attributen|
|-----------------------------------|
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [erstellen Sie ein Windows Forms-Benutzersteuerelement die Suche Datenbindung unterstützenden](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet. Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie ein neues **Windows Forms-Anwendung**.

- Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.

- Entwerfen des Benutzersteuerelements im visuellen Designer.

- Implementieren des `ComplexBindingProperty`-Attributs.

- Erstellen Sie ein Dataset mit dem [Datenquellen Konfigurations-Assistenten](../data-tools/media/data-source-configuration-wizard.png).

- Festlegen der **Kunden** -Tabelle in der [Datenquellenfenster](add-new-data-sources.md) des neuen komplexen Steuerelements verwenden.

- Fügen Sie das neue Steuerelement durch Ziehen aus dem **Datenquellenfenster** auf **Form1**.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.

1. Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.

1. Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .

       Ein Abfrage-Editorfenster wird geöffnet.

    1. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    1. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen Sie eine Windows Forms-Anwendung

 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.

### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .

1. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows Desktop**.

1. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

1. Nennen Sie das Projekt **ComplexControlWalkthrough**, und wählen Sie dann **OK**.

    Die **ComplexControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt

Da in dieser exemplarischen Vorgehensweise ein komplexes, datenbindbares Steuerelement aus erstellt eine **Benutzersteuerelement**, müssen Sie hinzufügen, eine **Benutzersteuerelement** Element aus, um das Projekt.

### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu

1. Aus der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.

1. Typ **ComplexDataGridView** in der **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.

    Die **ComplexDataGridView** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.

## <a name="design-the-complexdatagridview-control"></a>Entwerfen des ComplexDataGridView-Steuerelements

Dieser Schritt fügt dem Benutzersteuerelement eine <xref:System.Windows.Forms.DataGridView> hinzu.

### <a name="to-design-the-complexdatagridview-control"></a>So entwerfen Sie das ComplexDataGridView-Steuerelement

- Ziehen Sie eine <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.

## <a name="add-the-required-data-binding-attribute"></a>Hinzufügen des erforderlichen Datenbindungsattributs

Für komplexe Steuerelemente, die Datenbindung unterstützen, können Sie das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren.

### <a name="to-implement-the-complexbindingproperties-attribute"></a>So implementieren Sie das ComplexBindingProperties-Attribut

1. Wechseln der **ComplexDataGridView** -Steuerelement zur Codeansicht. (Auf der **Ansicht** klicken Sie im Menü **Code**.)

1. Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="creating-a-data-source-from-your-database"></a>Erstellen eine Datenquelle aus einer Datenbank

Dieser Schritt wird mithilfe der **Datenquellenkonfiguration** -Assistenten zum Erstellen einer Datenquelle basierend auf der `Customers` Tabelle in der Northwind-Beispieldatenbank.

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** (Dialogfeld).

5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.

    Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die `Customers` Tabelle wird angezeigt, der **Datenquellen** Fenster.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Festlegen der Tabelle "Customers", verwenden Sie das ComplexDataGridView-Steuerelement

Innerhalb der **Datenquellen** können Sie das Steuerelement erstellt werden soll, vor dem Ziehen von Elementen auf das Formular festlegen.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>So legen Sie die Bindung der Spalte Customers an das ComplexDataGridView-Steuerelement fest

1. Open **Form1** im Designer.

1. Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.

1. Klicken Sie auf den Dropdown Pfeil auf der **Kunden** Knoten, und wählen Sie **anpassen**.

1. Wählen Sie die **ComplexDataGridView** aus der Liste der **zugeordnete Steuerelemente** in der **Optionen für die Anpassung der Datenbenutzeroberfläche** (Dialogfeld).

1. Klicken Sie auf den Dropdown Pfeil auf der `Customers` Tabelle, und wählen Sie **ComplexDataGridView** aus der Steuerungsliste.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular

Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.

### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular

Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular. Überprüfen Sie, ob die **ComplexDataGridView** Steuerelement wird verwendet, um die Daten der Tabelle angezeigt.

## <a name="running-the-application"></a>Ausführen der Anwendung

### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

Drücken Sie F5, um die Anwendung auszuführen.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:

- Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.

- Erstellen von Steuerelementen, die Nachschlageszenarien unterstützen. Weitere Informationen finden Sie unter [erstellen Sie ein Windows Forms-Benutzersteuerelement die Suche Datenbindung unterstützenden](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index)