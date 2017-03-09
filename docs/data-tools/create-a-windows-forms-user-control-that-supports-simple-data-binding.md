---
title: "Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das einfache Datenbindung unterst&#252;tzt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "Benutzerdefinierte Steuerelemente [Visual Studio], Datenquellenfenster"
  - "Datenquellenfenster, Steuerelemente"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das einfache Datenbindung unterst&#252;tzt
Zum Anzeigen von Daten in Formularen in Windows\-Anwendungen können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder – falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist – benutzerdefinierte Steuerelemente erstellen.  Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert.  Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann.  Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.  
  
 Weitere Informationen zum Erstellen von Steuerelementen finden Sie unter [Entwickeln von Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:  
  
|Verwendung von Datenbindungsattributen|  
|--------------------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte \(oder Eigenschaft\) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>\-Steuerelement.  \(Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.\)|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen \(oder Tabellen\) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>\-Steuerelement.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen \(oder Tabellen\) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt.  In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet.  Das einfache Benutzersteuerelement zeigt die Telefonnummern des Kunden in einem standardmäßigen Telefonnummernformat mithilfe einer <xref:System.Windows.Forms.MaskedTextBox> und dem Festlegen der Maske auf eine Telefonnummer.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie eine neue **Windows\-Anwendung**.  
  
-   Hinzufügen eines neuen **Benutzersteuerelements** zu einem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `DefaultBindingProperty`\-Attributs.  
  
-   Erstellen eines Datasets mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Legen Sie für die Spalte **Telefon** im Fenster **Datenquellen** fest, dass das neue Steuerelement verwendet wird.  
  
-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.  
  
2.  Geben Sie dem Projekt den Namen **SimpleControlWalkthrough**.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **SimpleControlWalkthrough** wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Hinzufügen eines Benutzersteuerelements zum Projekt  
 Diese exemplarische Vorgehensweise erstellt ein einfaches, datenbindbares Steuerelement aus einem **Benutzersteuerelement**. Fügen Sie deshalb ein **Benutzersteuerelement** dem Projekt **SimpleControlWalkthrough** hinzu.  
  
#### So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie im Menü **Projekt** den Punkt **Benutzersteuerelement hinzufügen**.  
  
2.  Geben Sie `PhoneNumberBox` in den Bereich Name ein und klicken Sie auf **Hinzufügen**.  
  
     Das **PhoneNumberBox**\-Steuerelement wird dem **Projektmappen\-Explorer** hinzugefügt und im Designer geöffnet.  
  
## Entwerfen des PhoneNumberBox\-Steuerelements  
 Diese exemplarische Vorgehensweise erweitert das vorhandene <xref:System.Windows.Forms.MaskedTextBox>, sodass das `PhoneNumberBox`\-Steuerelement erstellt wird.  
  
#### Entwerfen des PhoneNumberBox\-Steuerelements  
  
1.  Ziehen Sie ein <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
2.  Wählen Sie den Smart Tag auf dem <xref:System.Windows.Forms.MaskedTextBox>, das Sie gerade herein gezogen haben und wählen Sie **Maske festlegen**.  
  
3.  Wählen Sie **Telefonnummer** im Dialogfeld **Eingabeformat** und klicken Sie **OK**, um die Maske festzulegen.  
  
## Hinzufügen des erforderlichen Datenbindungsattributs  
 Implementieren Sie für einfache Steuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### So implementieren Sie das Attribut DefaultBindingProperty  
  
1.  Wechseln Sie für das `PhoneNumberBox`\-Steuerelement zur Codeansicht.  \(Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.\)  
  
2.  Ersetzen Sie den Code in `PhoneNumberBox` durch folgenden Code:  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.  
  
## Erstellen einer Datenquelle aus einer Datenbank  
 Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Customers`\-Tabelle in der Beispieldatenbank Northwind.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         Oder  
  
    -   Wählen Sie **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die `Customers`\-Tabelle und klicken Sie anschließend auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabelle `Customers` wird im **Datenquellenfenster** angezeigt.  
  
## Festlegen, dass die Spalte "Telefon" das Steuerelement PhoneNumberBox verwendet  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### So legen Sie die Bindung der Spalte "Telefon" an das PhoneNumberBox\-Steuerelement fest  
  
1.  Öffnen Sie **Form1** im Designer.  
  
2.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3.  Klicken Sie auf den Dropdownpfeil auf dem Knoten **Customers** und wählen Sie **Details** aus der Steuerungsliste.  
  
4.  Klicken Sie den Dropdownpfeil auf der Spalte **Kunden** und wählen Sie **Anpassen**.  
  
5.  Wählen Sie im **Optionen für die Anpassung der Datenbenutzeroberfläche** in der Liste **Zugeordnete Steuerelemente** den Eintrag **PhoneNumberBox** aus.  
  
6.  Klicken Sie den Dropdownpfeil auf der Spalte **Kunden** und wählen Sie **PhoneNumberBox**.  
  
## Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** auf das Formular und achten Sie darauf, dass das Steuerelement `PhoneNumberBox` zur Anzeige der Spalte `Phone` verwendet wird.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen.  Zu den typischen nächsten Schritten gehören Folgende:  
  
-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
-   Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) und [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Siehe auch  
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)