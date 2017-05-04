---
title: "Gewusst wie: Auff&#252;llen von Dokumenten mit Daten von Objekten | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Auffüllen mit Daten"
  - "Daten [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gewusst wie: Auff&#252;llen von Dokumenten mit Daten von Objekten
  Der Zugriff auf Daten in einem Datenobjekt funktioniert in Microsoft Office Word\-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms\-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einem Objekt in die Projektmappe einzufügen, und können Windows Forms\-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Sie müssen drei grundlegende Schritte ausführen, um das Dokument mit Daten aus einem Objekt aufzufüllen:  
  
-   Fügen Sie ein Steuerelement zum Dokument hinzu, das an Daten gebunden werden kann.  
  
-   Fügen Sie ein Datenobjekt zum Dokument hinzu.  
  
-   Verbinden Sie das Datenobjekt mit der BindingSource\-Komponente.  
  
## Hinzufügen eines Datenobjekts  
  
#### So fügen Sie ein Datenobjekt hinzu  
  
-   Öffnen Sie das Fenster **Datenquellen**, und erstellen Sie eine Datenquelle auf Grundlage eines Objekts. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in Objekten](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).  
  
## Verbinden des Datenobjekts mit der BindingSource\-Komponente  
 In Projekten auf Dokumentebene fügen Sie Ihrem Dokument Steuerelemente hinzu und binden diese zur Entwurfszeit an Daten.  
  
 In VSTO\-Add\-In\-Projekten erstellen Sie Steuerelemente und binden diese zur Laufzeit.  
  
### Projekte auf Dokumentebene  
  
##### So verbinden Sie das Datenobjekt mit der BindingSource\-Komponente  
  
1.  Ziehen Sie das gewünschte Datenfeld vom Fenster **Datenquellen** in Ihr Dokument. Dadurch wird automatisch ein Steuerelement erstellt.  
  
2.  Erstellen Sie im Code eine Instanz des Typs des Objekts, das Sie für die Datenquelle ausgewählt haben.  
  
3.  Weisen Sie die Instanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A>\-Eigenschaft der <xref:System.Windows.Forms.BindingSource>\-Komponente zu.  
  
### Projekte auf Anwendungsebene  
  
##### So verbinden Sie das Datenobjekt mit der BindingSource\-Komponente  
  
1.  Erstellen Sie im Code eine Instanz des Typs des Objekts, das der Datenquelle zugewiesen wird.  
  
2.  Erstellen Sie eine Instanz einer <xref:System.Windows.Forms.BindingSource>\-Komponente:  
  
3.  Weisen Sie die Datenquelleninstanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A>\-Eigenschaft der <xref:System.Windows.Forms.BindingSource>\-Komponente zu.  
  
4.  Fügen Sie die Datenquelle als eine Datenbindung zum Steuerelement hinzu.  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  