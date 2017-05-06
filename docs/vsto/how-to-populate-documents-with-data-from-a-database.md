---
title: "Gewusst wie: Auff&#252;llen von Dokumenten mit Daten aus einer Datenbank"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Daten, Hinzufügen zu Dokumenten"
  - "Dokumente, Auffüllen mit Daten"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Auff&#252;llen von Dokumenten mit Daten aus einer Datenbank
  Sie können in Microsoft Office\-Projekten auf Dokumentebene auf die gleiche Weise auf Daten zugreifen wie in Windows Forms\-Projekten.  Sie verwenden dieselben Tools und denselben Code, um die Daten aus einer Datenbank in die Projektmappe einzufügen, und können Windows Forms\-Steuerelemente zum Anzeigen der Daten verwenden.  
  
 Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen.  Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden.  Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen.  Ein Beispiel dazu, wie Sie datengebundene Steuerelemente in VSTO\-Add\-In\-Projekten zur Laufzeit hinzufügen, finden Sie unter [Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projek](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Binden von Daten an Word 2007\-Inhaltssteuerelemente mit den Visual Studio\-Tools für Office System \(3.0\)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## Hinzufügen eines Steuerelements zu einem Dokument zur Entwurfszeit  
  
#### So füllen Sie ein Dokument mit Daten aus einer Datenbank auf  
  
1.  Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Word\-Projekt auf Dokumentebene, während das Dokument im Designer geöffnet ist.  
  
2.  Öffnen Sie das Fenster **Datenquellen**, und erstellen Sie eine Datenquelle auf Grundlage einer Datenbank.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Ziehen Sie das gewünschte Feld vom Fenster **Datenquellen** in Ihr Dokument.  
  
 Ein Inhaltssteuerelement wird dem Dokument hinzugefügt.  Der Typ des Inhaltssteuerelements hängt vom Datentyp des ausgewählten Felds ab.  Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
 Sie können ein anderes Steuerelement hinzufügen, indem Sie das Datenfeld im Fenster **Datenquellen** und dann ein anderes Steuerelement in der Dropdownliste auswählen.  
  
## Objekte im Projekt  
 Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:  
  
-   Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben.  Weitere Informationen finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird.  Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
-   Eine TableAdapter, durch die das typisierte Dataset mit der Datenbank verbunden wird.  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
-   Ein TableAdapterManager dient zum Koordinieren von Tabellenadaptern im Dataset, um hierarchische Updates zu ermöglichen.  Weitere Informationen finden Sie unter [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md) und [Übersicht über TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an.  Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.  
  
#### So führen Sie einen Bildlauf durch die Datensätze durch  
  
-   Verwenden Sie <xref:System.Windows.Forms.BindingSource>\-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Informationen zum Senden von Updates an das typisierte Dataset und die Datenbank finden Sie unter [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Übersicht über die Verwendung lokaler Datenbankdateien in Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  