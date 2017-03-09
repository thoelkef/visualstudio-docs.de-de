---
title: "Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das eine Datenbindung beim Suchen unterst&#252;tzt | Microsoft Docs"
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
  - "Datenbindung, Benutzersteuerelemente"
  - "LookupBindingPropertiesAttribute-Klasse, Beispiele"
  - "Benutzersteuerelemente [Visual Basic], Erstellen"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen eines Windows Forms-Benutzersteuerelements, das eine Datenbindung beim Suchen unterst&#252;tzt
Zum Anzeigen von Daten in Windows Forms können Sie die in der Toolbox vorhandenen Steuerelemente verwenden oder – falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist – benutzerdefinierte Steuerelemente erstellen.  Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementiert.  Steuerelemente, die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementieren, können drei Eigenschaften enthalten, die an Daten gebunden werden können.  Solche Steuerelemente ähneln einem <xref:System.Windows.Forms.ComboBox>\-Steuerelement.  
  
 Weitere Informationen zum Erstellen von Steuerelementen finden Sie unter [Entwickeln von Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:  
  
|Verwendung von Datenbindungsattributen|  
|--------------------------------------------|  
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte \(oder Eigenschaft\) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>\-Steuerelement.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen \(oder Tabellen\) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>\-Steuerelement.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementieren Sie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> für Steuerelemente, die Listen \(oder Tabellen\) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, wie das <xref:System.Windows.Forms.ComboBox>\-Steuerelement.  \(Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.\)|  
  
 In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement erstellt, das an Daten aus zwei Tabellen gebunden ist.  In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  Das Nachschlagesteuerelement wird an das Feld `CustomerID` der Tabelle `Orders` gebunden.  Das Steuerelement verwendet diesen Wert, um in der Tabelle `Customers` den entsprechenden Wert von `CompanyName` nachzuschlagen.  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie eine neue **Windows\-Anwendung**.  
  
-   Hinzufügen eines neuen **Benutzersteuerelements** zu einem Projekt.  
  
-   Entwerfen des Benutzersteuerelements im visuellen Designer.  
  
-   Implementieren des `LookupBindingProperty`\-Attributs.  
  
-   Erstellen eines Datasets mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Festlegen der Spalte **CustomerID** aus der Tabelle **Orders** auf die Verwendung des neuen Steuerelements \(im **Datenquellenfenster**\).  
  
-   Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.  
  
2.  Geben Sie dem Projekt den Namen LookupControlWalkthrough.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **LookupControlWalkthrough** wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Hinzufügen eines Benutzersteuerelements zum Projekt  
 In dieser exemplarischen Vorgehensweise wird aus einem **Benutzersteuerelement** ein Nachschlagesteuerelement erstellt. Fügen Sie dem Projekt **LookupControlWalkthrough** zunächst also ein **Benutzersteuerelement** hinzu.  
  
#### So fügen Sie dem Projekt ein Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2.  Geben Sie im Bereich **Name** die Bezeichnung `LookupBox` ein, und klicken Sie auf **Hinzufügen**.  
  
     Das **LookupBox**\-Steuerelement wird dem **Projektmappen\-Explorer** hinzugefügt und im Designer geöffnet.  
  
## Entwerfen des LookupBox\-Steuerelements  
  
#### So entwerfen Sie das LookupBox\-Steuerelement  
  
-   Ziehen Sie ein <xref:System.Windows.Forms.ComboBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.  
  
## Hinzufügen des erforderlichen Datenbindungsattributs  
 Implementieren Sie für Nachschlagesteuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### So implementieren Sie das LookupBindingProperties\-Attribut  
  
1.  Wechseln Sie für das **LookupBox**\-Steuerelement zur Codeansicht.  \(Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.\)  
  
2.  Ersetzen Sie den Code in `LookupBox` durch folgenden Code:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.  
  
## Erstellen einer Datenquelle aus einer Datenbank  
 In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle erstellt, die auf den Tabellen `Customers` und `Orders` der Beispieldatenbank Northwind basiert.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im **Datenquellenfenster** angezeigt.  
  
## Festlegen der Spalte "CustomerID" aus der Tabelle "Orders" auf die Verwendung des LookupBox\-Steuerelements  
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.  
  
#### So legen Sie die Bindung der Spalte "CustomerID" an das LookupBox\-Steuerelement fest  
  
1.  Öffnen Sie **Form1** im Designer.  
  
2.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
3.  Erweitern Sie den Knoten **Orders** \(denjenigen, der sich im Knoten **Customers** unterhalb der Spalte **Fax** befindet\).  
  
4.  Klicken Sie im Knoten **Orders** auf den Dropdownpfeil, und wählen Sie in der Steuerelementliste die Option **Details** aus.  
  
5.  Klicken Sie in der Spalte **CustomerID** \(im Knoten **Orders**\) auf den Dropdownpfeil, und wählen Sie **Anpassen** aus.  
  
6.  Wählen Sie im Dialogfeld **Optionen für die Anpassung der Datenbenutzeroberfläche** in der Liste **Zugeordnete Steuerelemente** den Eintrag **LookupBox** aus.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie in der Spalte **CustomerID** auf den Dropdownpfeil, und wählen Sie **LookupBox** aus.  
  
## Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf **Form1** ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Windows Form  
  
-   Ziehen Sie den Knoten **Orders** aus dem **Datenquellenfenster** auf das Windows Form, und stellen Sie sicher, dass das **LookupBox**\-Steuerelement zum Anzeigen der Daten in der Spalte `CustomerID` verwendet wird.  
  
## Binden des Steuerelements für das Nachschlagen von CompanyName in der Tabelle Customers  
  
#### So richten Sie die Nachschlagebindungen ein  
  
-   Wählen Sie im **Datenquellenfenster** den Hauptknoten **Customers** aus, und ziehen Sie ihn auf das Kombinationsfeld in **CustomerIDLookupBox** von **Form1**.  
  
     Damit wird die Datenbindung so eingerichtet, dass der Wert für `CompanyName` aus der Tabelle `Customers` angezeigt und gleichzeitig der Wert für `CustomerID` aus der Tabelle `Orders` beibehalten wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Nachschlagetabellen in Windows Forms\-Anwendungen](../data-tools/create-lookup-tables-in-windows-forms-applications.md).  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
-   Navigieren Sie durch einige Datensätze, und prüfen Sie, ob im `LookupBox`\-Steuerelement der Wert von `CompanyName` angezeigt wird.  
  
## Siehe auch  
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)