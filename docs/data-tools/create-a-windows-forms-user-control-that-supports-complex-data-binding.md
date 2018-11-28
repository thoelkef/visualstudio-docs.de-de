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
ms.openlocfilehash: 7de5cbfe7de8919143cd30517c18f9e5ad6ba598
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305246"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt

Zum Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie die in der Toolbox** vorhandenen Steuerelemente verwenden oder – falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist – benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.

Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelemente zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung Attributverwendung|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet. Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie eine neue Windows Forms-Anwendung.

- Hinzufügen eines neuen Benutzersteuerelements** zu einem Projekt.

- Entwerfen des Benutzersteuerelements im visuellen Designer.

- Implementieren des `ComplexBindingProperty`-Attributs.

- Erstellen eines Datasets mit dem [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png).

- Legen Sie die **Kunden** -Tabelle in der [Fenster "Datenquellen"](add-new-data-sources.md#data-sources-window) auf das neue, komplexe Steuerelement verwendet.

- Fügen Sie das neue Steuerelement hinzu, indem Sie es vom Datenquellenfenster **auf Form1** ziehen.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

1. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    1. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    1. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung.

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**:

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

1. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

1. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

1. Nennen Sie das Projekt **ComplexControlWalkthrough**, und wählen Sie dann **OK**.

    Das Projekt ComplexControlWalkthrough **wird erstellt und zum Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement hinzu.

Da in dieser exemplarischen Vorgehensweise ein komplexes, datenbindbares Steuerelement aus erstellt eine **Benutzersteuerelement**, Hinzufügen einer **Benutzersteuerelement** Elements zum Projekt:

1. Wählen Sie im Menü Projekt **den Punkt Benutzersteuerelement hinzufügen**.

1. Geben Sie ComplexDataGridView in den Bereich Name **ein und klicken Sie anschließend auf Hinzufügen**.

    Das ComplexDataGridView **-Steuerelement wird dem Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.

## <a name="design-the-complexdatagridview-control"></a>Entwerfen des ComplexDataGridView-Steuerelements

Hinzufügen einer <xref:System.Windows.Forms.DataGridView> auf das Benutzersteuerelement, ziehen Sie eine <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.

## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu

Für komplexe Steuerelemente, die Datenbindung unterstützen, können Sie das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren.

1. Wechseln Sie für das ComplexDataGridView **-Steuerelement zur Codeansicht. (Wählen Sie aus dem Menü Ansicht **den Punkt Code**.)

1. Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank

Verwenden der **Datenquellenkonfiguration** Assistenten zum Erstellen einer Datenquelle basierend auf den `Customers` Tabelle in der Northwind-Beispieldatenbank:

1.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

2.  Wählen Sie im Datenquellenfenster **die Option Neue Datenquelle hinzufügen** aus, um den Assistenten zum Konfigurieren von Datenquellen** zu starten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Führen Sie auf der Seite Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Wählen Sie Neue Verbindung **, um das Dialogfeld Verbindung hinzufügen/ändern** zu öffnen.

5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf Weiter **.

6.  Klicken Sie auf der Seite Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern **auf Weiter**.

7.  Erweitern Sie auf der Seite Datenbankobjekte auswählen **den Knoten Tabellen**.

8.  Wählen Sie die `Customers`-Tabelle und klicken Sie anschließend auf Fertig stellen **.

    NorthwindDataSet**wird dem Projekt hinzugefügt. Die Tabelle** wird im Datenquellenfenster`Customers` angezeigt.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Festlegen der Tabelle Customers das Steuerelement ComplexDataGridView verwendet

Im Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.

1. Öffnen Sie Form1** im Designer.

1. Erweitern Sie im Datenquellenfenster **den Knoten Customers**.

1. Klicken Sie den Dropdown-Pfeil auf dem Knoten Customers **und wählen Sie Anpassen**.

1. Wählen Sie im Dialogfeld Optionen für die Anpassung der Datenbenutzeroberfläche **in der Liste Zugeordnete Steuerelemente** den Eintrag ComplexDataGridView** aus.

1. Klicken Sie auf den Dropdownpfeil auf der `Customers`-Tabelle und wählen Sie ComplexDataGridView** aus der Steuerungsliste.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zu dem Formular.

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Datenquellenfenster** auf das Formular ziehen. Ziehen Sie den Hauptknoten Customers **aus dem Datenquellenfenster** in das Formular. Überprüfen Sie, ob die **ComplexDataGridView** Steuerelement wird verwendet, um die Daten der Tabelle angezeigt.

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um die Anwendung auszuführen.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:

- Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.

- Erstellen von Steuerelementen, die Nachschlageszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index)