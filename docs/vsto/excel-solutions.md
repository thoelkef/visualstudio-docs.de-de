---
title: "Excel-Projektmappen | Microsoft Docs"
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
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Excel"
  - "Excel [Office-Entwicklung in Visual Studio], Add-Ins auf Anwendungsebene"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Excel"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Excel"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Excel"
  - "Excel [Office-Entwicklung in Visual Studio], Informationen zu Excel-Projektmappen"
  - "Excel [Office-Entwicklung in Visual Studio]"
  - "Dokumente [Office-Entwicklung in Visual Studio], Excel"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Excel"
  - "Projekte [Office-Entwicklung in Visual Studio], Excel"
  - "Excel [Office-Entwicklung in Visual Studio], Anpassungen auf Dokumentebene"
  - "Benutzeroberflächen [Office-Entwicklung in Visual Studio], Excel"
  - "Office-Entwicklung in Visual Studio, Excel-Projektmappen"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Excel"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Excel"
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Excel-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie verwenden können, um Anpassungen auf Dokumentebene und VSTO\-Add\-Ins für Microsoft Office Excel zu erstellen. Mit diesen Projektmappen können Sie Excel automatisieren, Excel\-Features erweitern und die Excel\-Benutzeroberfläche anpassen. Weitere Informationen zu den Unterschieden zwischen Anpassungen auf Dokumentebene und VSTO\-Add\-Ins finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Automatisieren von Excel](#automating)  
  
-   [Entwickeln von Anpassungen auf Dokumentebene für Excel](#doclevel)  
  
-   [Entwickeln von VSTO\-Add\-Ins für Excel](#applevel)  
  
-   [Anpassen der Excel\-Benutzeroberfläche](#UI)  
  
##  <a name="automating"></a> Automatisieren von Excel  
 Das Excel\-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Excel verwenden können. Beispielsweise können Sie programmgesteuert Diagramme erstellen, Arbeitsblätter formatieren und die Werte von Bereichen und Zellen festlegen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
 Wenn Sie Excel\-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente* in den Projektmappen verwenden. Dabei handelt es sich um Objekte, die bestimmte häufig verwendete Objekte im Excel\-Objektmodell erweitern, z. B. das <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt und das <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt. Die erweiterten Objekte verhalten sich wie die Excel\-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis\- und Datenbindungsfunktionen hinzu. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Entwickeln von Anpassungen auf Dokumentebene für Excel  
 Eine Anpassung auf Dokumentebene für Microsoft Office Excel besteht aus einer Assembly, die einer spezifischen Arbeitsmappe zugeordnet ist. Die Assembly erweitert das Dokument normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Im Gegensatz zu einem VSTO\-Add\-In, das Excel direkt zugeordnet ist, sind Funktionen, die in einer Anpassung implementiert werden, nur dann verfügbar, wenn die zugehörige Arbeitsmappe in Word geöffnet ist.  
  
 Um ein Anpassungsprojekt auf Dokumentebene für Excel zu erstellen, verwenden Sie die Projektvorlagen für Excel\-Arbeitsmappen oder Excel\-Vorlagen im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Weitere Informationen zur Funktionsweise von Anpassungen auf Dokumentebene finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
### Programmiermodell für die Anpassung von Excel  
 Wenn Sie ein Projekt auf Dokumentebene für Excel erstellen, generiert Visual Studio mehrere Klassen, die die Grundlage für die Projektmappe bilden: `ThisWorkbook`, `Sheet1`, `Sheet2` und `Sheet3`. Diese Klassen stellen die Arbeitsmappe und die Arbeitsblätter dar, die der Projektmappe zugeordnet sind, und sie bieten einen Ausgangspunkt zum Schreiben von Code.  
  
 Weitere Informationen zu diesen generierten Klassen und zu anderen Funktionen, die Sie in einem Projekt auf Dokumentebene verwenden können, finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Entwickeln von VSTO\-Add\-Ins für Excel  
 Ein VSTO\-Add\-In für Microsoft Office Excel besteht aus einer Assembly, die von Excel geladen wird. Die Assembly erweitert Excel normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Im Gegensatz zu einer Anpassung auf Dokumentebene, die einer bestimmten Arbeitsmappe zugeordnet wird, sind Funktionen, die in einem VSTO\-Add\-In implementiert werden, nicht auf eine einzelne Arbeitsmappe beschränkt.  
  
 Um ein VSTO\-Add\-In\-Projekt für Excel zu erstellen, verwenden Sie die Projektvorlagen für Excel\-Arbeitsmappen oder Excel\-Vorlagen im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Allgemeine Informationen über die Funktionsweise von VSTO\-Add\-Ins finden Sie unter [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [How Do I: Automate PowerPoint from an Excel Add\-in?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### Add\-In\-Programmiermodell von Excel  
 Wenn Sie ein Excel\-VSTO\-Add\-In\-Projekt erstellen, generiert Visual Studio eine Klasse namens `ThisAddIn`, die die Grundlage der Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben von Code, und sie macht auch das Excel\-Objektmodell für das VSTO\-Add\-In verfügbar.  
  
 Weitere Informationen zur `ThisAddIn`\-Klasse und anderen Visual Studio\-Features, die Sie in einem VSTO\-Add\-In verwenden können, finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Anpassen der Excel\-Benutzeroberfläche  
 Es gibt mehrere Möglichkeiten, die Benutzeroberfläche von Excel anzupassen. Einige Optionen sind für alle Projekttypen verfügbar, andere Optionen sind jedoch nur für VSTO\-Add\-Ins oder Anpassungen auf Dokumentebene verfügbar.  
  
### Optionen für alle Projekttypen  
 In der folgenden Tabelle sind die Anpassungsoptionen aufgeführt, die sowohl für Anpassungen auf Dokumentebene als auch für VSTO\-Add\-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Anpassen des Menübands|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
|Hinzufügen von Windows Forms\-Steuerelementen oder erweiterten Excel\-Steuerelementen zu einem Arbeitsblatt in der angepassten Arbeitsmappe \(für eine Anpassung auf Dokumentebene\) oder zu einer beliebigen geöffneten Arbeitsmappe \(für ein VSTO\-Add\-In\).|[Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Gewusst wie: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### Optionen für Anpassungen auf Dokumentebene  
 In der folgenden Tabelle sind Anpassungsoptionen aufgeführt, die nur für Anpassungen auf Dokumentebene zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Fügen Sie der Arbeitsmappe einen Aktionsbereich hinzu.|[Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)<br /><br /> [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Fügen Sie einem Arbeitsblatt erweiterte Bereichssteuerelemente hinzu, die XML\-Knoten zugeordnet sind.|[Gewusst wie: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### Optionen für VSTO\-Add\-Ins  
 In der folgenden Tabelle werden Anpassungsoptionen aufgeführt, die nur für VSTO\-Add\-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
  
### Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)|Hier finden Sie eine Übersicht über die wichtigsten Typen im Excel\-Objektmodell.|  
|[Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)|Hier finden Sie Informationen zu erweiterten Objekten \(der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]\), die in Excel\-Projektmappen verwendet werden können.|  
|[Globalisierung und Lokalisierung von Excel-Lösungen](../vsto/globalization-and-localization-of-excel-solutions.md)|Enthält besondere Überlegungen zu Excel\-Projektmappen, die auf Computern ausgeführt werden, die über nicht englische Einstellungen für Windows verfügen.|  
|[Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)|Hier wird beschrieben, wie Sie Excel\-Arbeitsblättern Windows Forms\-Steuerelemente hinzufügen können.|  
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen.|  
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Veranschaulicht die Erstellung eines grundlegenden VSTO\-Add\-Ins für Excel.|  
|[Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-Ad-In-Projekt](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Veranschaulicht, wie Sie einem Arbeitsblatt zur Laufzeit mithilfe eines VSTO\-Add\-Ins eine Windows Forms\-Schaltfläche, ein <xref:Microsoft.Office.Tools.Excel.NamedRange> und ein <xref:Microsoft.Office.Tools.Excel.ListObject> hinzufügen können.|  
|[Excel 2010 unter Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199011)|Enthält Links zu Artikeln und Referenzdokumentation zur Entwicklung von Excel\-Projektmappen. Diese sind nicht spezifisch für die Office\-Entwicklung mit Visual Studio.|  
  
  