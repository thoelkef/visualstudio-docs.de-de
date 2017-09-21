---
title: "Binden von Windows Forms-Steuerelementen an Daten in Visual Studio | Microsoft Docs"
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
  - "Daten [Windows Forms], Datenquellen"
  - "Daten [Windows Forms], Anzeigen"
  - "Datenquellen, Anzeigen von Daten"
  - "Anzeigen von Daten auf Formularen"
  - "Anzeigen von Daten, Windows Forms"
  - "Formulare, Anzeigen von Daten"
  - "Windows Forms, Datenbindung"
  - "Windows Forms, Anzeigen von Daten"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Binden von Windows Forms-Steuerelementen an Daten in Visual Studio
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Windows Forms binden.  Zum Erstellen dieser datengebundenen Steuerelemente können Sie Elemente aus dem **Datenquellenfenster** in den Windows Forms\-Designer in Visual Studio ziehen.  In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, die beim Erstellen von datengebundenen Anwendungen verwendet werden.  
  
 Allgemeine Informationen zum Erstellen von datengebundenen Steuerelementen in Visual Studio finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  Weitere Informationen zur Datenbindung in Windows Forms finden Sie unter [Datenbindung in Web Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Aufgaben beim Anzeigen von Daten in einem Formular einer Windows\-Anwendung  
 In der folgenden Tabelle werden gängige Aufgaben aufgeführt, die sich auf das Anzeigen von Daten auf einem Formular in einer Windows\-Anwendung beziehen.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Erstellen Sie datengebundene Steuerelemente.<br /><br /> Binden Sie vorhandenen Steuerelemente an Daten.|[Gewusst wie: Binden von Windows Forms\-Steuerelementen an Daten](../data-tools/bind-windows-forms-controls-to-data.md)|  
|Erstellen Sie Steuerelemente, die verknüpfte Daten in Beziehungen zwischen übergeordneten und untergeordneten Elementen anzeigen: Wenn der Benutzer einen Datensatz in einem Steuerelement auswählt, werden in einem anderen Steuerelement verknüpfte Daten für den ausgewählten Datensatz angezeigt.|[Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)|  
|Erstellen Sie eine *Suchtabelle*.  Eine Suchtabelle dient der Anzeige von Informationen aus einer Tabelle auf der Grundlage des Werts eines Fremdschlüsselfelds in einer anderen Tabelle.|[Gewusst wie: Erstellen von Nachschlagetabellen in Windows Forms\-Anwendungen](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|Formatieren Sie die Darstellung von Steuerelementdaten.|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/de-de/42638120-9e6f-436b-985f-4036664230fd)|  
|Ändern Sie das Verhalten der Smart\-Captioning\-Funktion im **Datenquellenfenster**.|[Gewusst wie: Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|Fügen Sie Steuerelemente hinzu, die eine parametrisierte Abfrage ausführen.|[Gewusst wie: Hinzufügen einer parametrisierten Abfrage zu einem Formular in einer Windows Forms\-Anwendung](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|Legen Sie eine Spalte für die Verwendung einer Bildsteuerung fest, um Bilder in einer Datenbank anzuzeigen.|[Gewusst wie: Binden von Steuerelementen an Bilder aus einer Datenbank](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|Filtern oder sortieren Sie Daten in einem Dataset.|[Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms\-Anwendung](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 Die folgenden Themen enthalten Beispiele für das Binden von Windows Forms\-Steuerelementen an Daten.  
  
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 Enthält schrittweise aufgebaute Details zum Abfragen von Daten aus einer Datenbank und zum Anzeigen der Daten in einem Windows Form.  
  
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einem Windows Form](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md)  
 Enthält schrittweise aufgebaute Details zum Anzeigen der Daten aus zwei verknüpften Tabellen und zum Anzeigen der Daten in einem Windows Form.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms zum Suchen von Daten](../data-tools/create-a-windows-form-to-search-data.md)  
 Stellt anschauliche Details zum Erstellen eines Windows\-Formulars bereit, das auf Grundlage der Benutzereingabe eine Datenbanksuche durchführt.  
  
 [Exemplarische Vorgehensweise: Erstellen einer Suchtabelle in einer Windows Forms\-Anwendung](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 Enthält ausführliche schrittweise Anleitungen zum Anzeigen von Daten aus einer Tabelle, die auf den in einer anderen Tabelle ausgewählten Daten basiert.  
  
 [Exemplarische Vorgehensweise: Übergeben von Daten zwischen Windows Forms](../data-tools/pass-data-between-forms.md)  
 Enthält Schritt\-für\-Schritt\-Anweisungen zum Übergeben von Werten aus einem Formular an ein anderes Formular in der Anwendung.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 Stellt Schritt\-für\-Schritt\-Anweisungen zum Erstellen eines benutzerdefinierten Steuerelements bereit, das im Fenster **Datenquellen** verwendet werden kann.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 Stellt Schritt\-für\-Schritt\-Anweisungen zum Erstellen eines benutzerdefinierten Steuerelements bereit, das im Fenster **Datenquellen** verwendet werden kann.  
  
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 Stellt Schritt\-für\-Schritt\-Anweisungen zum Erstellen eines benutzerdefinierten Steuerelements bereit, das im Fenster **Datenquellen** verwendet werden kann.  
  
## Smarttags für Daten  
 Bei zahlreichen Steuerelementen stehen bestimmte Smarttags zum Bearbeiten von Daten zur Verfügung.  Sobald einem Formular bestimmte Steuerelemente hinzugefügt werden, steht im Smarttag eine Reihe möglicher datenbezogener Aktionen zur Verfügung.  
  
## BindingSource\-Komponente  
 Die <xref:System.Windows.Forms.BindingSource>\-Komponente dient zwei Zwecken.  Erstens stellt sie eine Abstraktionsebene bereit, wenn die Steuerelemente auf dem Formular an Daten gebunden werden.  Steuerelemente auf dem Formular werden an die <xref:System.Windows.Forms.BindingSource>\-Komponente gebunden \(also nicht direkt an eine Datenquelle\).  
  
 Zweitens kann so eine Auflistung von Objekten verwaltet werden.  Wenn Sie zur <xref:System.Windows.Forms.BindingSource>\-Komponente einen Typ hinzuzufügen, wird eine Liste dieses Typs erstellt.  
  
 Weitere Informationen über die <xref:System.Windows.Forms.BindingSource>\-Komponente finden Sie unter:  
  
-   [BindingSource\-Komponente](../Topic/BindingSource%20Component.md)  
  
-   [Übersicht über die BindingSource\-Komponente](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Architektur der BindingSource\-Komponente](../Topic/BindingSource%20Component%20Architecture.md)  
  
## BindingNavigator\-Steuerelement  
 Diese Komponente stellt eine Benutzeroberfläche zum Navigieren durch Daten bereit, die von einer Windows\-Anwendung angezeigt werden.  Weitere Informationen finden Sie unter [BindingNavigator\-Steuerelement](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## DataGridView\-Steuerelement  
 Mit dem <xref:System.Windows.Forms.DataGridView>\-Steuerelement können Sie Tabellendaten aus vielen unterschiedlichen Datenquellen anzeigen und bearbeiten.  Sie können Daten mit der <xref:System.Windows.Forms.DataGridView.DataSource%2A>\-Eigenschaft an ein <xref:System.Windows.Forms.DataGridView>\-Element binden.  Weitere Informationen finden Sie unter [Übersicht über das DataGridView\-Steuerelement](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Windows Forms\-Benutzersteuerelements, das eine Datenbindung beim Suchen unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)