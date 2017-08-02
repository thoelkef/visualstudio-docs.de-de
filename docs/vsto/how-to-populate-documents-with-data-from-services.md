---
title: "Gewusst wie: Auff&#252;llen von Dokumente mit Daten aus Diensten"
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
  - "Webdienste [Office-Entwicklung in Visual Studio], Füllen von Dokumenten"
  - "Daten [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gewusst wie: Auff&#252;llen von Dokumente mit Daten aus Diensten
  Der Datenzugriff funktioniert in Microsoft Office\-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms\-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms\-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie von so genannten Hoststeuerelemente profitieren – systemeigene Objekte in Microsoft Office Excel und Microsoft Office Word, die um Ereignisse und Datenbindungsfunktionen erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Das folgende Beispiel zeigt, wie Sie Dokumenten zur Entwurfszeit datengebundene Steuerelemente hinzufügen. Ein Beispiel für das Hinzufügen von datengebundenen Steuerelementen in VSTO\-Add\-Ins zur Laufzeit finden Sie unter [Exemplarische Vorgehensweise: Binden an Daten aus einem Dienst in einem VSTO-Add-In-Projekt](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![Link zu Video](~/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Anleitung: Interagieren mit Webdiensten aus Microsoft Excel](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### So füllen Sie ein Projekt auf Dokumentebene mit Daten aus einem Webdienst auf  
  
1.  Öffnen Sie das Fenster **Datenquellen**, und erstellen Sie für Ihr Projekt eine Dienstdatenquelle. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst](~/data-tools/how-to-connect-to-data-in-a-service.md).  
  
2.  Ziehen Sie die gewünschte Tabelle oder das gewünschte Feld vom Fenster **Datenquellen** in Ihr Dokument.  
  
     Im Dokument wird ein Steuerelement erstellt. Zudem werden für den Dienst eine an die Objektklassen des Projekts gebundene <xref:System.Windows.Forms.BindingSource> und Klassen generiert.  
  
3.  Erstellen Sie im Code eine Instanz der Webdienstklasse, zu der in Schritt 1 eine Verbindung hergestellt wurde.  
  
4.  Wenn für die Kommunikation mit dem Webdienst Eigenschaften erforderlich sind, erstellen Sie Instanzen dieser Eigenschaften.  
  
5.  Erstellen und senden Sie mithilfe der vom Webdienst bereitgestellten Methoden und der in Schritt 4 erstellten Dateninstanzen eine Datenanforderung.  
  
     Welche Methoden verwendet werden, ist abhängig vom Angebot des Webdiensts.  
  
6.  Weisen Sie die Datenantwort des Webdiensts der Eigenschaft <xref:System.Windows.Forms.BindingSource.DataSource%2A> der <xref:System.Windows.Forms.BindingSource> zu.  
  
 Wenn Sie das Projekt ausführen, zeigen die Steuerelemente den ersten Datensatz in der Datenquelle an. Sie können einen Bildlauf durch die Datensätze ermöglichen, indem Sie die „Currency“\-Ereignisse mit den Objekten in der <xref:System.Windows.Forms.BindingSource> verarbeiten.  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  