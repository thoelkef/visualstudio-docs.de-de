---
title: "Gewusst wie: Auff&#252;llen von Arbeitsbl&#228;ttern mit Daten aus einer Datenbank | Microsoft Docs"
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
  - "Daten [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "Datenbanken [Office-Entwicklung in Visual Studio], Auffüllen von Arbeitsblättern"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio], Auffüllen"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Gewusst wie: Auff&#252;llen von Arbeitsbl&#228;ttern mit Daten aus einer Datenbank
  Sie können Daten in Office\-Projekten auf Dokumentebene projizieren genauso, dass bei Windows Forms\-Projekt.  Sie verwenden dieselben Tools und denselben Code, um die Daten in Ihre Lösung einzufügen, und Sie können zum Anzeigen der Daten sogar Steuerelemente für Windows Forms verwenden.  Zudem können Sie die als Hoststeuerelemente bezeichneten Steuerelemente nutzen. Dabei handelt es sich um systemeigene Objekte in Microsoft Office Excel, die um Ereignisse und Datenbindungsfunktionen erweitert wurden.  Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe eines Designers in Projekten auf Dokumentebene datengebundene Steuerelemente hinzugefügt werden.  Ein Beispiel zum Hinzufügen von datengebundenen Steuerelementen in Projekten auf Anwendungsebene zur Laufzeit finden Sie unter [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-Add-In-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie in den Themen zur [Übertragung von Daten in ein Excel\-Arbeitsblatt](http://go.microsoft.com/fwlink/?LinkID=130277) und zur [Nutzung von Datenbankdaten in Excel](http://go.microsoft.com/fwlink/?LinkID=130287) \(möglicherweise in englischer Sprache\).  
  
## Hinzufügen eines datengebundenen Steuerelements zu einem Arbeitsblatt zur Entwurfszeit  
  
#### So füllen Sie ein Arbeitsblatt mit Daten aus einer Datenbank auf  
  
1.  Öffnen Sie in Visual Studio ein Projekt auf Dokumentebene für Excel. Dabei ist das Arbeitsblatt im Designer geöffnet.  
  
2.  Öffnen Sie das **Datenquellenfenster**, und erstellen Sie für Ihr Projekt eine Datenquelle.  Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Ziehen Sie das gewünschte Feld oder die gewünschte Tabelle vom **Datenquellenfenster** in das Arbeitsblatt.  
  
 Eines der folgenden Steuerelemente wird im Arbeitsblatt erstellt:  
  
-   Wenn Sie ein Feld ziehen, wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement im Arbeitsblatt erstellt.  Weitere Informationen finden Sie unter [NamedRange-Steuerelement](../vsto/namedrange-control.md).  
  
-   Wenn Sie eine Tabelle ziehen, wird ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement im Arbeitsblatt erstellt.  Weitere Informationen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
 Sie können ein anderes Steuerelement hinzufügen, indem Sie im Fenster **Datenquellen** die Tabelle oder das Feld und anschließend in der Dropdownliste ein anderes Steuerelement auswählen.  
  
## Objekte im Projekt  
 Neben dem Steuerelement werden dem Projekt die folgenden datenbezogenen Objekte automatisch hinzugefügt:  
  
-   Ein typisiertes Dataset, das die Datentabellen kapselt, zu denen Sie in der Datenbank eine Verbindung hergestellt haben.  Weitere Informationen finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Eine <xref:System.Windows.Forms.BindingSource>, die das Steuerelement mit dem typisierten Dataset verbindet.  Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](../Topic/BindingSource%20Component%20Overview.md).  
  
-   Ein TableAdapter, der das typisierte Dataset mit der Datenbank verbindet.  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
-   Ein TableAdapterManager, der verwendet wird, um Tabellenadapter im Dataset zu koordinieren und so hierarchische Updates zu aktivieren.  Weitere Informationen finden Sie unter [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md) und [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Wenn Sie das Projekt ausführen, zeigt das Steuerelement den ersten Datensatz in der Datenquelle an.  Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um es Benutzern zu ermöglichen, einen Bildlauf durch die Datensätze durchzuführen.  
  
#### So führen Sie den Bildlauf durch die Datensätze aus  
  
-   Verwenden Sie <xref:System.Windows.Forms.BindingSource>\-Methoden, beispielsweise <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Informationen zum Senden von Updates an das typisierte Dataset und die Datenbank finden Sie unter [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumente mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wie behebe ich: Daten in einem Excel\-Arbeitsblatt](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Wie behebe ich: Nutzen Sie Datenbankdaten in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  