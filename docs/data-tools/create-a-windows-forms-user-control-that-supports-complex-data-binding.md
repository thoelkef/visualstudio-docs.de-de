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
ms.openlocfilehash: db8059cf34c2de9a52cda18dd09ce6040bf8d841
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937901"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt

Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandenen Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.

Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelemente zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Beim Erstellen von Steuerelementen für die Verwendung in Szenarios mit Datenbindung müssen Sie eine der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung Attributverwendung|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt. In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet. Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie ein neues **Windows Forms-Anwendung**.

- Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.

- Entwerfen des Benutzersteuerelements im visuellen Designer.

- Implementieren des `ComplexBindingProperty`-Attributs.

- Erstellen eines Datasets mit dem [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png).

- Legen Sie die **Kunden** -Tabelle in der [Fensters "Datenquellen"](add-new-data-sources.md) auf das neue, komplexe Steuerelement verwendet.

- Fügen Sie das neue Steuerelement durch Ziehen aus dem **Fensters "Datenquellen"** auf **Form1**.

## <a name="prerequisites"></a>Vorraussetzungen

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

1. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    1. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    1. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**:

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

1. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

1. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

1. Nennen Sie das Projekt **ComplexControlWalkthrough**, und wählen Sie dann **OK**.

    Die **ComplexControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement

Da in dieser exemplarischen Vorgehensweise ein komplexes, datenbindbares Steuerelement aus erstellt eine **Benutzersteuerelement**, Hinzufügen einer **Benutzersteuerelement** Elements zum Projekt:

1. Von der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.

1. Typ **ComplexDataGridView** in die **Namen** Bereich, und klicken Sie dann auf **hinzufügen**.

    Die **ComplexDataGridView** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.

## <a name="design-the-complexdatagridview-control"></a>Entwerfen des ComplexDataGridView-Steuerelements

Hinzufügen einer <xref:System.Windows.Forms.DataGridView> auf das Benutzersteuerelement, ziehen Sie eine <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.

## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu

Für komplexe, Datenbindung unterstützen Steuerelemente, können Sie implementieren die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Wechseln der **ComplexDataGridView** -Steuerelement zur Codeansicht. (Auf der **Ansicht** , wählen Sie im Menü **Code**.)

1. Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank

Verwenden der **Datenquellenkonfiguration** Assistenten zum Erstellen einer Datenquelle basierend auf den `Customers` Tabelle in der Northwind-Beispieldatenbank:

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.

5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.

    Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die `Customers` Tabelle angezeigt wird, der **Datenquellen** Fenster.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Festlegen der Tabelle Customers das Steuerelement ComplexDataGridView verwendet

In der **Datenquellen** Fenster können Sie das Steuerelement erstellt werden, vor dem Ziehen von Elementen auf das Formular festlegen:

1. Open **Form1** im Designer.

1. Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.

1. Klicken Sie auf die Dropdown-Pfeil der **Kunden** Knoten, und wählen Sie **anpassen**.

1. Wählen Sie die **ComplexDataGridView** aus der Liste der **zugeordnete Steuerelemente** in die **Optionen für die Anpassung** Dialogfeld.

1. Klicken Sie auf die Dropdown-Pfeil der `Customers` Tabelle, und wählen Sie **ComplexDataGridView** aus der Steuerungsliste.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular

Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular. Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular. Überprüfen Sie, ob die **ComplexDataGridView** Steuerelement wird verwendet, um die Daten der Tabelle angezeigt.

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