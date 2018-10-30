---
title: Erstellen eines Benutzersteuerelements, das die einfache Datenbindung unterstützt
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f5bffba1b2de64c142dd70990fb74429ad40269a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220094"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das einfache Datenbindung unterstützt

Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandenen Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.

Weitere Informationen über das Erstellen von Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Bei der Erstellung von Steuerelementen für die Verwendung in Szenarios mit Datenbindung müssen Sie eine der folgenden Datenbindungsattribute implementieren:

|Die Datenbindung Attributverwendung|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt. In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet. Das einfache Benutzersteuerelement zeigt die Telefonnummern von Kunden in einem Standardformat von Telefonnummern mithilfe einer <xref:System.Windows.Forms.MaskedTextBox> und Festlegen der Maske auf eine Telefonnummer an.

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

-   Erstellen Sie ein neues **Windows Forms-Anwendung**.

-   Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.

-   Entwerfen des Benutzersteuerelements im visuellen Designer.

-   Implementieren des `DefaultBindingProperty`-Attributs.

-   Erstellen eines Datasets mit dem **Datenquellenkonfiguration** Assistenten.

-   Legen Sie die **Phone** -Spalte in der **Datenquellen** Fenster, das das neue Steuerelement verwendet.

-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.

## <a name="prerequisites"></a>Vorraussetzungen

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** arbeitsauslastung in der **Visual Studio-Installer**.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**:

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **SimpleControlWalkthrough**, und wählen Sie dann **OK**.

     Die **SimpleControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-user-control-to-the-project"></a>Fügen Sie dem Projekt ein Benutzersteuerelement

In dieser exemplarischen Vorgehensweise erstellt ein einfaches, datenbindbares Steuerelement aus einem **Benutzersteuerelement**. Hinzufügen einer **Benutzersteuerelement** Element für die **SimpleControlWalkthrough** Projekt:

1.  Von der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.

2.  Typ **PhoneNumberBox** in den Bereich Name ein und klicken Sie auf **hinzufügen**.

     Die **PhoneNumberBox** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.

## <a name="design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements

Diese exemplarische Vorgehensweise baut auf den vorhandenen <xref:System.Windows.Forms.MaskedTextBox> zum Erstellen der **PhoneNumberBox** Steuerelement:

1.  Ziehen Sie eine <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf der Entwurfsoberfläche des Benutzersteuerelements.

2.  Wählen Sie auf das Smarttag die <xref:System.Windows.Forms.MaskedTextBox> gerade gezogen haben, und klicken Sie **Maske festlegen**.

3.  Wählen Sie **Telefonnummer** in die **Eingabeformat** (Dialogfeld), und klicken Sie auf **OK** zum Festlegen der Maske.

## <a name="add-the-required-data-binding-attribute"></a>Fügen Sie das erforderliche Attribut für die Datenbindung hinzu

Für einfache-, die Datenbindung unterstützen Steuerelemente, implementieren die <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Wechseln der **PhoneNumberBox** -Steuerelement zur Codeansicht. (Auf der **Ansicht** Menü wählen **Code**.)

2.  Ersetzen Sie den Code in die **PhoneNumberBox** durch Folgendes:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank

Dieser Schritt verwendet den **Datenquellenkonfiguration** Assistenten zum Erstellen einer Datenquelle basierend auf den `Customers` -Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.

3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** eine der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.

5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.

     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die `Customers` Tabelle angezeigt wird, der **Datenquellen** Fenster.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Festlegen der Spalte "Phone" auf das Steuerelement PhoneNumberBox verwendet

In der **Datenquellen** Fenster können Sie das Steuerelement erstellt werden, vor dem Ziehen von Elementen auf das Formular festlegen:

1.  Open **Form1** im Designer.

2.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.

3.  Klicken Sie auf die Dropdown-Pfeil der **Kunden** Knoten, und wählen Sie **Details** aus der Steuerungsliste.

4.  Klicken Sie auf die Dropdown-Pfeil der **Phone** Spalte, und wählen Sie **anpassen**.

5.  Wählen Sie die **PhoneNumberBox** aus der Liste der **zugeordnete Steuerelemente** in die **Optionen für die Anpassung** Dialogfeld.

6.  Klicken Sie auf die Dropdown-Pfeil der **Phone** Spalte, und wählen Sie **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular

Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.

Ziehen Sie den Hauptknoten, um datengebundene Steuerelemente auf dem Formular zu erstellen, **Kunden** Knoten aus der **Datenquellen** auf das Formular, und überprüfen Sie, ob die **PhoneNumberBox** Steuerelement zum Anzeigen der Daten in die **Phone** Spalte.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um die Anwendung auszuführen.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:

-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.

-   Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) und [Erstellen eines Windows Forms-Benutzersteuerelements, die Bindung an Nachschlagedaten unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)