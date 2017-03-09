---
title: "Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterst&#252;tzt | Microsoft Docs"
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
  - "Datenbindung, Komplex"
  - "Datenbindung, Benutzersteuerelemente"
  - "Benutzersteuerelemente [Visual Studio], Komplexe Datenbindung"
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterst&#252;tzt
Zum Anzeigen von Daten in Formularen in Windows\-Anwendungen können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder – falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist – benutzerdefinierte Steuerelemente erstellen.  Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementiert.  Steuerelemente, die <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren, enthalten eine Eigenschaft `DataSource` und `DataMember`, die an Daten gebunden werden kann.  Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.DataGridView> oder <xref:System.Windows.Forms.ListBox>.  
  
 Weitere Informationen zum Erstellen von Steuerelementen finden Sie unter [Entwickeln von Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:  
  
|Verwendung von Datenbindungsattributen|  
|--------------------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte \(oder Eigenschaft\) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>\-Steuerelement.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen \(oder Tabellen\) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>\-Steuerelement.  \(Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.\)|  
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen \(oder Tabellen\) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 In dieser exemplarischen Vorgehensweise wird ein Steuerelement erstellt, das Datenzeilen aus einer Tabelle darstellt.  In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet.  Das komplexe Benutzersteuerelement stellt die Tabelle Customers in einer <xref:System.Windows.Forms.DataGridView> im benutzerdefinierten Steuerelement dar.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie eine neue **Windows\-Anwendung**.  
  
-   Hinzufügen eines neuen **Benutzersteuerelements** zu einem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `ComplexBindingProperty`\-Attributs.  
  
-   Erstellen eines Datasets mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Legt fest, dass die Tabelle **Customers** im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) das neue, komplexe Steuerelement verwendet.  
  
-   Fügen Sie das neue Steuerelement hinzu, indem Sie es vom **Datenquellenfenster** auf **Form1** ziehen.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.  
  
2.  Geben Sie dem Projekt den Namen ComplexControlWalkthrough.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **ComplexControlWalkthrough** wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Hinzufügen eines Benutzersteuerelements zum Projekt  
 Weil diese exemplarische Vorgehensweise ein komplexes, datenbindbares Steuerelement aus einem **Benutzersteuerelement** erstellt, müssen Sie dem Projekt ein **Benutzersteuerelement** hinzufügen.  
  
#### So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie im Menü **Projekt** den Punkt **Benutzersteuerelement hinzufügen**.  
  
2.  Geben Sie ComplexDataGridView in den Bereich **Name** ein und klicken Sie anschließend auf **Hinzufügen**.  
  
     Das **ComplexDataGridView**\-Steuerelement wird dem **Projektmappen\-Explorer** hinzugefügt und im Designer geöffnet.  
  
## Entwerfen des ComplexDataGridView\-Steuerelements  
 Dieser Schritt fügt dem Benutzersteuerelement eine <xref:System.Windows.Forms.DataGridView> hinzu.  
  
#### So entwerfen Sie das ComplexDataGridView\-Steuerelement  
  
-   Ziehen Sie ein <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
## Hinzufügen des erforderlichen Datenbindungsattributs  
 Für komplexe Steuerelemente, die Datenbindung unterstützen, können Sie das <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> implementieren.  
  
#### So implementieren Sie das ComplexBindingProperties\-Attribut  
  
1.  Wechseln Sie für das **ComplexDataGridView**\-Steuerelement zur Codeansicht.  \(Wählen Sie aus dem Menü **Ansicht** den Punkt **Code**.\)  
  
2.  Ersetzen Sie den Code in `ComplexDataGridView` durch folgenden Code:  
  
     [!code-cs[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.  
  
## Erstellen einer Datenquelle aus einer Datenbank  
 Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Customers`\-Tabelle in der Beispieldatenbank Northwind.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die `Customers`\-Tabelle und klicken Sie anschließend auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabelle `Customers` wird im **Datenquellenfenster** angezeigt.  
  
## Festlegen, dass die Spalte Customers das Steuerelement ComplexDataGridView verwendet  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### So legen Sie die Bindung der Spalte Customers an das ComplexDataGridView\-Steuerelement fest  
  
1.  Öffnen Sie **Form1** im Designer.  
  
2.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3.  Klicken Sie den Dropdown\-Pfeil auf dem Knoten **Customers** und wählen Sie **Anpassen**.  
  
4.  Wählen Sie im Dialogfeld **Optionen für die Anpassung der Datenbenutzeroberfläche** in der Liste **Zugeordnete Steuerelemente** den Eintrag **ComplexDataGridView** aus.  
  
5.  Klicken Sie auf den Dropdownpfeil auf der `Customers`\-Tabelle und wählen Sie **ComplexDataGridView** aus der Steuerungsliste.  
  
## Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** auf das Formular und achten Sie darauf, dass das Steuerelement **ComplexDataGridView** zur Anzeige der Daten in der Tabelle verwendet wird.  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen.  Zu den typischen nächsten Schritten gehören Folgende:  
  
-   Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.  
  
-   Erstellen von Steuerelementen, die Nachschlageszenarien unterstützen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Siehe auch  
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms\-Steuerelemente](../Topic/Windows%20Forms%20Controls.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)