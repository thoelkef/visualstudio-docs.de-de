---
title: "Erstellen eines Benutzersteuerelements, das einfache Datenbindung unterstützt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 63df502f17a5c85e51e658854d2ab7dec312fcc5
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das einfache Datenbindung unterstützt
Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie vorhandene Steuerelemente aus der **Toolbox**, oder Sie können benutzerdefinierte Steuerelemente erstellen, wenn Ihre Anwendung Funktionen erfordert, die in den Standardsteuerelementen nicht verfügbar ist. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.  
  
 Weitere Informationen zu Steuerelementen, finden Sie unter [Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 Bei der Erstellung von Steuerelementen für die Verwendung in Datenbindungsszenarien sollten Sie eine der folgenden Datenbindungsattribute implementieren:  
  
|Die Datenbindung-Attributen|  
|-----------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [erstellen Sie ein Windows Forms-Benutzersteuerelement die Suche Datenbindung unterstützenden](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt. In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet. Das einfache Benutzersteuerelement zeigt Telefonnummern des Kunden in einem standardmäßigen Telefonnummernformat mithilfe einer <xref:System.Windows.Forms.MaskedTextBox> und Festlegen der Maske auf eine Telefonnummer.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie ein neues **Windows Forms-Anwendung**.  
  
-   Fügen Sie einen neuen **Benutzersteuerelement** zu Ihrem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `DefaultBindingProperty`-Attributs.  
  
-   Erstellen Sie ein Dataset mit dem **Datenquellenkonfiguration** Assistenten.  
  
-   Legen Sie die **Phone** Spalte in der **Datenquellen** Fenster, das das neue Steuerelement verwendet.  
  
-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **SimpleControlWalkthrough**, und wählen Sie dann **OK**. 
  
     Die **SimpleControlWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt  
 In dieser exemplarischen Vorgehensweise erstellt ein einfaches, datenbindbares Steuerelement aus einer **Benutzersteuerelement**, fügen Sie daher eine **Benutzersteuerelement** Element zum der **SimpleControlWalkthrough** Projekt.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Aus der **Projekt** Menü wählen **Benutzersteuerelement hinzufügen**.  
  
2.  Typ `PhoneNumberBox` in den Bereich Name ein und klicken Sie auf **hinzufügen**.  
  
     Die **PhoneNumberBox** -Steuerelement hinzugefügt **Projektmappen-Explorer**, und im Designer geöffnet.  
  
## <a name="design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
 Diese exemplarische Vorgehensweise erweitert das vorhandene <xref:System.Windows.Forms.MaskedTextBox>, sodass das `PhoneNumberBox`-Steuerelement erstellt wird.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements  
  
1.  Ziehen Sie eine <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
2.  Wählen Sie auf das Smarttag der <xref:System.Windows.Forms.MaskedTextBox> Sie gerade gezogen haben, und wählen Sie **Maske festlegen**.  
  
3.  Wählen Sie **Telefonnummer** in der **Eingabeformat** (Dialogfeld), und klicken Sie auf **OK** zum Festlegen der Maske.  
  
## <a name="add-the-required-data-binding-attribute"></a>Hinzufügen des erforderlichen Datenbindungsattributs  
 Implementieren Sie für einfache Steuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>So implementieren Sie das Attribut DefaultBindingProperty  
  
1.  Wechseln Sie für das `PhoneNumberBox`-Steuerelement zur Codeansicht. (Auf der **Ansicht** Menü wählen **Code**.)  
  
2.  Ersetzen Sie den Code in `PhoneNumberBox` durch folgenden Code:  
  
     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.  
  
## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank  
 Dieser Schritt wird mithilfe der **Datenquellenkonfiguration**-Assistenten zum Erstellen einer Datenquelle basierend auf der `Customers` Tabelle in der Northwind-Beispieldatenbank. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Northwind-Beispieldatenbank finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite, führen Sie eine der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** (Dialogfeld).  
  
5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die `Customers` Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die `Customers` Tabelle wird angezeigt, der **Datenquellen** Fenster.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Festlegen der Spalte "Phone" mithilfe des PhoneNumberBox-Steuerelements  
 Innerhalb der **Datenquellen** können Sie das Steuerelement erstellt werden soll, vor dem Ziehen von Elementen auf das Formular festlegen.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>So legen Sie die Bindung der Spalte "Telefon" an das PhoneNumberBox-Steuerelement fest  
  
1.  Open **Form1** im Designer.  
  
2.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
3.  Klicken Sie auf den Dropdown Pfeil auf der **Kunden** Knoten, und wählen Sie **Details** aus der Steuerungsliste.  
  
4.  Klicken Sie auf den Dropdown Pfeil auf der **Phone** Spalte, und wählen Sie **anpassen**.  
  
5.  Wählen Sie die **PhoneNumberBox** aus der Liste der **zugeordnete Steuerelemente** in der **Optionen für die Anpassung der Datenbenutzeroberfläche** (Dialogfeld).  
  
6.  Klicken Sie auf den Dropdown Pfeil auf der **Phone** Spalte, und wählen Sie **PhoneNumberBox**.  
  
## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf das Formular, und überprüfen Sie, ob die `PhoneNumberBox` Steuerelement wird verwendet, um die Anzeige der Daten in der `Phone` Spalte.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:  
  
-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
-   Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) und [erstellen Sie ein Windows Forms-Benutzersteuerelement die Suche Datenbindung unterstützenden](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
