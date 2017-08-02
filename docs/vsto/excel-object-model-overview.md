---
title: "&#220;bersicht &#252;ber das Excel-Objektmodell"
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
  - "Excel-Objektmodell"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Excel"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Office"
  - "Objekte [Office-Entwicklung in Visual Studio], Office-Objektmodelle"
  - "Office-Objektmodelle"
  - "Range-Objekt"
  - "Workbook-Klasse"
  - "Worksheet-Objekt"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 65
---
# &#220;bersicht &#252;ber das Excel-Objektmodell
  Zum Entwickeln von Lösungen, die Microsoft Office Excel verwenden, können Sie mit den Objekten des Excel\-Objektmodells interagieren.  In diesem Thema werden die wichtigsten Objekte vorgestellt:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Das Objektmodell orientiert sich stark an der Benutzeroberfläche.  Das <xref:Microsoft.Office.Interop.Excel.Application>\-Objekt stellt die gesamte Anwendung dar, und jedes <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt enthält eine Auflistung von `Worksheet`\-Objekten.  Davon ausgehend gibt es als bedeutende Abstraktion das <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt, das Zellen darstellt und für die Arbeit mit einzelnen Zellen oder Zellgruppen verwendet werden kann.  
  
 Zusätzlich zum Excel\-Objektmodell stellen Office\-Projekte in Visual Studio *Hostelemente* und *Hoststeuerelemente* bereit, die im Excel\-Objektmodell einige Objekte erweitern.  Hostelemente und Hoststeuerelemente verhalten sich wie die Excel\-Objekte, dass sie erweitern, verfügen jedoch auch über zusätzliche Funktionen, z. B. Datenbindungsfunktionen und zusätzliche Ereignisse.  Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md) und [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 Dieses Thema enthält eine kurze Übersicht über das Excel\-Objektmodell.  Informationen zu Ressourcen, in denen Sie mehr über das gesamte Excel\-Objektmodell erfahren, finden Sie unter [Verwenden der Dokumentation zum Excel\-Objektmodell](#ExcelOMDocumentation).  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden von Ereignishandlern in einem Excel 2007 Add\-In](http://go.microsoft.com/fwlink/?LinkID=130291) und [Gewusst wie: Verwenden von Formen zum Erstellen eines Blasendiagramms in Excel](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## Zugreifen auf Objekte in einem Excel\-Projekt  
 Beim Erstellen eines neuen VSTO\-Add\-In\-Projekts erstellt Visual Studio automatisch die Codedatei „ThisAddIn.vb“ oder „ThisAddIn.cs“.  Sie können mithilfe von `Me.Application` oder `this.Application` auf das Anwendungsobjekt zugreifen.  
  
 Wenn Sie ein neues Projekt auf Dokumentebene für Excel erstellen, haben Sie die Möglichkeit, eine neue Excel\-Arbeitsmappe oder ein Excel\-Vorlagenprojekt zu erstellen.  Visual Studio erstellt die folgenden Codedateien im neuen Excel\-Projekt sowohl für Arbeitsmappen\- als auch für Vorlagenprojekte automatisch.  
  
|Visual Basic|C\#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Mit der `Globals`\-Klasse im Projekt können Sie auf `ThisWorkbook`, `Sheet1`, `Sheet2` oder `Sheet3` von außerhalb der jeweiligen Klasse zugreifen.  Weitere Informationen finden Sie unter [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  Im folgenden Beispiel wird die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>\-Methode von `Sheet1` aufgerufen, und zwar unabhängig davon, ob der Code in einer der `Sheet`*n*\-Klassen oder in der `ThisWorkbook`\-Klasse platziert wird.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#82)]  
  
 Da die Daten in einem Excel\-Dokument sehr strukturiert sind, ist das Objektmodell hierarchisch und unkompliziert.  Excel enthält hunderte von Objekten, mit denen Sie interagieren können. Als Einstieg in das Objektmodell empfiehlt es sich jedoch, sich zunächst auf eine sehr kleine Teilmenge der verfügbaren Objekte zu konzentrieren.  Dazu gehören die folgenden vier Objekte:  
  
-   Anwendung  
  
-   Arbeitsmappe  
  
-   Arbeitsblatt  
  
-   Bereich  
  
 Diese vier Objekte und ihre Member decken einen Großteil der Aufgaben ab, die mit Excel erledigt werden können.  
  
### Anwendungsobjekt  
 Beim <xref:Microsoft.Office.Interop.Excel.Application>\-Objekt von Excel handelt es sich um die eigentliche Excel\-Anwendung.  Das <xref:Microsoft.Office.Interop.Excel.Application>\-Objekt stellt zahlreiche Informationen über die ausgeführte Anwendung, die auf diese Instanz angewendeten Optionen und die derzeit darin geöffneten Benutzerobjekte zur Verfügung.  
  
> [!NOTE]  
>  Sie sollten die <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Excel.Application>\-Objekts in Excel nicht auf **false** festlegen.  Wenn Sie diese Eigenschaft auf „false“ festlegen, kann Excel keine Ereignisse auslösen, auch nicht die Ereignisse von Hoststeuerelementen.  
  
### Arbeitsmappenobjekt  
 Das <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt stellt eine einzelne Arbeitsmappe innerhalb der Excel\-Anwendung dar.  
  
 Die Office\-Entwicklungstools in Visual Studio erweitern das <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt, indem sie den <xref:Microsoft.Office.Tools.Excel.Workbook>\-Typ bereitstellen.  Dieser Typ bietet Zugriff auf alle Funktionen eines <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekts.  Weitere Informationen finden Sie unter [Arbeitsmappenhostelement](../vsto/workbook-host-item.md).  
  
### Arbeitsblattobjekt  
 Das <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt ist ein Member der <xref:Microsoft.Office.Interop.Excel.Worksheets>\-Auflistung.  Viele der Eigenschaften, Methoden und Ereignisse der <xref:Microsoft.Office.Interop.Excel.Worksheet> sind identisch oder ähneln den Membern der <xref:Microsoft.Office.Interop.Excel.Application>\- oder <xref:Microsoft.Office.Interop.Excel.Workbook>\- Objekte.  
  
 Excel stellt eine <xref:Microsoft.Office.Interop.Excel.Sheets>\-Auflistung als Eigenschaft eines <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekts bereit.  Bei jedem Member der <xref:Microsoft.Office.Interop.Excel.Sheets>\-Auflistung handelt es sich entweder um ein <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt oder ein <xref:Microsoft.Office.Interop.Excel.Chart>\-Objekt.  
  
 Die Office\-Entwicklungstools in Visual Studio erweitern das <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt, indem sie den <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Typ bereitstellen.  Dieser Typ gibt Ihnen Zugriff auf alle Funktionen eines <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekts sowie auf neue Funktionen, z. B. die Fähigkeit, verwaltete Steuerelemente zu hosten und neue Ereignisse zu behandeln.  Weitere Informationen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  
  
### Bereichsobjekt  
 Mit dem <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt werden Sie in den Excel\-Anwendungen am häufigsten arbeiten.  Bevor Sie Änderungen an einer Region in Excel vornehmen können, müssen Sie diese als <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt ausdrücken und mit den Methoden und Eigenschaften dieses Bereichs arbeiten.  Ein <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt stellt eine Zelle, eine Zeile, eine Spalte, eine Auswahl von Zellen, die entweder zusammenhängend oder unzusammenhängend sein können, oder sogar eine Gruppe von Zellen auf mehreren Arbeitsblättern dar.  
  
 Visual Studio erweitert das <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt durch Bereitstellen des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Typs und des <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Typs.  Diese Typen verfügen größtenteils über die gleichen Funktionen wie ein <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt sowie über neue Funktionen, z. B. die Datenbindungsfunktion und neue Ereignisse.  Weitere Informationen finden Sie unter [NamedRange-Steuerelement](../vsto/namedrange-control.md) und [XmlMappedRange-Steuerelement](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Verwenden der Dokumentation zum Excel\-Objektmodell  
 Ausführliche Informationen zum Excel\-Objektmodell finden Sie in der Referenz für die primäre Interopassembly \(PIA\) für Excel und der VBA\-Objektmodellreferenz.  
  
### Referenz für die primäre Interopassembly  
 In der Referenzdokumentation für die Excel\-PIA werden die Typen in der primären Interopassembly für Excel beschrieben.  Diese Dokumentation ist unter [Referenz für die primäre Interopassembly für Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585) verfügbar.  
  
 Weitere Informationen zum Entwurf der Excel\-PIA, z. B. zu Unterschieden zwischen Klassen und Schnittstellen in der PIA und zur Implementierung von Ereignissen in der PIA, finden Sie in der [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### VBA\-Objektmodellreferenz  
 Die VBA\-Objektmodellreferenz dokumentiert das Excel\-Objektmodell, das für VBA \(Visual Basic for Applications\) verfügbar gemacht wird.  Weitere Informationen finden Sie unter [Excel 2010\-Objektmodell\-Verweis](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Alle Objekte und Member in der VBA\-Objektmodellreferenz entsprechen Typen und Membern in der Excel\-PIA.  Das Worksheet\-Objekt in der VBA\-Objektmodellreferenz entspricht z. B. dem <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt in der Excel\-PIA.  Obwohl die VBA\-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA\-Code in dieser Referenz in Visual Basic oder Visual C\# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Excel\-Projekt verwenden möchten.  
  
### Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Excel-Projektmappen](../vsto/excel-solutions.md)|Hier wird erläutert, wie Sie Anpassungen auf Dokumentebene und Add\-Ins auf Anwendungsebene für Microsoft Office Excel erstellen können.|  
|[Arbeiten mit Bereichen](../vsto/working-with-ranges.md)|Hier finden Sie Beispiele, die die Ausführung häufiger Aufgaben im Zusammenhang mit Bereichen veranschaulichen.|  
|[Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)|Hier finden Sie Beispiele, die die Ausführung häufiger Aufgaben im Zusammenhang mit Arbeitsblättern veranschaulichen.|  
|[Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)|Hier finden Sie Beispiele, die die Ausführung häufiger Aufgaben im Zusammenhang mit Arbeitsmappen veranschaulichen.|  
  
  