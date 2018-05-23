---
title: Excel-Lösungen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e2c6e25c3acdfb4c90eb0ba74d66670be339588
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="excel-solutions"></a>Excel-Lösungen
  Visual Studio stellt Projektvorlagen bereit, die Sie verwenden können, um Anpassungen auf Dokumentebene und VSTO-Add-Ins für Microsoft Office Excel zu erstellen. Mit diesen Projektmappen können Sie Excel automatisieren, Excel-Features erweitern und die Excel-Benutzeroberfläche anpassen. Weitere Informationen zu den Unterschieden zwischen Anpassungen auf Dokumentebene und VSTO-Add-ins finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Automatisieren von Excel](#automating).  
  
-   [Entwickeln von Anpassungen auf Dokumentebene für Excel](#doclevel).  
  
-   [Entwickeln von VSTO-Add-ins für Excel](#applevel).  
  
-   [Anpassen der Benutzeroberfläche von Excel](#UI).  
  
##  <a name="automating"></a> Automatisieren von Excel  
 Das Excel-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Excel verwenden können. Beispielsweise können Sie programmgesteuert Diagramme erstellen, Arbeitsblätter formatieren und die Werte von Bereichen und Zellen festlegen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
 Wenn Sie Excel-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente* in den Projektmappen verwenden. Dabei handelt es sich um Objekte, die bestimmte häufig verwendete Objekte im Excel-Objektmodell erweitern, z. B. das <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und das <xref:Microsoft.Office.Interop.Excel.Range> -Objekt. Die erweiterten Objekte verhalten sich wie die Excel-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis- und Datenbindungsfunktionen hinzu. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Entwickeln von Anpassungen auf Dokumentebene für Excel  
 Eine Anpassung auf Dokumentebene für Microsoft Office Excel besteht aus einer Assembly, die einer spezifischen Arbeitsmappe zugeordnet ist. Die Assembly erweitert das Dokument normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Im Gegensatz zu einem VSTO-Add-In, das Excel direkt zugeordnet ist, sind Funktionen, die in einer Anpassung implementiert werden, nur dann verfügbar, wenn die zugehörige Arbeitsmappe in Word geöffnet ist.  
  
 Um ein Anpassungsprojekt auf Dokumentebene für Excel erstellen, verwenden Sie die Excel-Arbeitsmappen oder Excel-Vorlagen-Projektvorlagen in den **neues Projekt** Dialogfeld von Visual Studio. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekte in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Weitere Informationen zur Anpassungen wie auf Dokumentebene finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Programmiermodell von Excel-Anpassung  
 Wenn Sie ein Projekt auf Dokumentebene für Excel erstellen, generiert Visual Studio mehrere Klassen, die die Grundlage für die Projektmappe bilden: `ThisWorkbook`, `Sheet1`, `Sheet2`und `Sheet3`. Diese Klassen stellen die Arbeitsmappe und die Arbeitsblätter dar, die der Projektmappe zugeordnet sind, und sie bieten einen Ausgangspunkt zum Schreiben von Code.  
  
 Weitere Informationen zu diesen generierten Klassen und andere Funktionen können in einem Projekt auf Dokumentebene finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Entwickeln von VSTO-Add-ins für Excel  
 Ein VSTO-Add-In für Microsoft Office Excel besteht aus einer Assembly, die von Excel geladen wird. Die Assembly erweitert Excel normalerweise durch das Anpassen der Benutzeroberfläche und das Automatisieren von Excel. Im Gegensatz zu einer Anpassung auf Dokumentebene, die einer bestimmten Arbeitsmappe zugeordnet wird, sind Funktionen, die in einem VSTO-Add-In implementiert werden, nicht auf eine einzelne Arbeitsmappe beschränkt.  
  
 Um ein VSTO-Add-in-Projekt für Excel erstellen, verwenden Sie die Excel-Arbeitsmappen oder Excel-Vorlagen-Projektvorlagen in den **neues Projekt** Dialogfeld von Visual Studio. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekte in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Allgemeine Informationen über die Funktionsweise von VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Automatisieren von PowerPoint von einem Excel-Add-in?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Excel-Add-in-Programmiermodell  
 Wenn Sie ein Excel-VSTO-Add-In-Projekt erstellen, generiert Visual Studio eine Klasse namens `ThisAddIn`, die die Grundlage der Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben von Code, und sie macht auch das Excel-Objektmodell für das VSTO-Add-In verfügbar.  
  
 Weitere Informationen zu den `ThisAddIn` -Klasse und anderen Visual Studio-Features Sie in einem VSTO-Add-in können finden Sie unter [Programm VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Anpassen der Benutzeroberfläche von Excel  
 Es gibt mehrere Möglichkeiten, die Benutzeroberfläche von Excel anzupassen. Einige Optionen sind für alle Projekttypen verfügbar, andere Optionen sind jedoch nur für VSTO-Add-Ins oder Anpassungen auf Dokumentebene verfügbar.  
  
### <a name="options-for-all-project-types"></a>Optionen für alle Projekttypen  
 In der folgenden Tabelle sind die Anpassungsoptionen aufgeführt, die sowohl für Anpassungen auf Dokumentebene als auch für VSTO-Add-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Anpassen des Menübands|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|  
|Hinzufügen von Windows Forms-Steuerelementen oder erweiterten Excel-Steuerelementen zu einem Arbeitsblatt in der angepassten Arbeitsmappe (für eine Anpassung auf Dokumentebene) oder zu einer beliebigen geöffneten Arbeitsmappe (für ein VSTO-Add-In).|[Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Optionen für Anpassungen auf Dokumentebene  
 In der folgenden Tabelle sind Anpassungsoptionen aufgeführt, die nur für Anpassungen auf Dokumentebene zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Fügen Sie der Arbeitsmappe einen Aktionsbereich hinzu.|[Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)<br /><br /> [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Fügen Sie einem Arbeitsblatt erweiterte Bereichssteuerelemente hinzu, die XML-Knoten zugeordnet sind.|[Vorgehensweise: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Optionen für VSTO-Add-Ins  
 In der folgenden Tabelle werden Anpassungsoptionen aufgeführt, die nur für VSTO-Add-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Verwandte Themen  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)|Hier finden Sie eine Übersicht über die wichtigsten Typen im Excel-Objektmodell.|  
|[Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)|Hier finden Sie Informationen zu erweiterten Objekten (der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), die in Excel-Projektmappen verwendet werden können.|  
|[Globalisierung und Lokalisierung von Excel-Projektmappen](../vsto/globalization-and-localization-of-excel-solutions.md)|Enthält besondere Überlegungen zu Excel-Projektmappen, die auf Computern ausgeführt werden, die über nicht englische Einstellungen für Windows verfügen.|  
|[Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)|Hier wird beschrieben, wie Sie Excel-Arbeitsblättern Windows Forms-Steuerelemente hinzufügen können.|  
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen.|  
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Veranschaulicht die Erstellung eines grundlegenden VSTO-Add-Ins für Excel.|  
|[Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in VSTO-Add-in-Projekt](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Veranschaulicht das Hinzufügen einer Windows Forms-Schaltfläche, eine <xref:Microsoft.Office.Tools.Excel.NamedRange>, und ein <xref:Microsoft.Office.Tools.Excel.ListObject> zu einem Arbeitsblatt zur Laufzeit mithilfe eines VSTO-Add-Ins.|
|[Verstehen Sie Co Authoring und Add-ins](./understanding-coauthoring-and-addins.md)|Beschreibt die Korrekturen, die Sie möglicherweise auf Ihre Lösungen stellen, um Mitverfasser Rechnung zu tragen.|  
|[Excel 2010 in Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199011)|Enthält Links zu Artikeln und Referenzdokumentation zur Entwicklung von Excel-Projektmappen. Diese sind nicht spezifisch für die Office-Entwicklung mit Visual Studio.|  
  
  