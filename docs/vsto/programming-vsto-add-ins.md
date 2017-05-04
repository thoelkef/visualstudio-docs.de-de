---
title: "Programmieren von VSTO-Add-Ins | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Addin"
  - "VST.ProjectItem.AddinProject"
  - "thisAddIn"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IcustomTaskPaneConsumer-Schnittstelle"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Programmierung"
  - "IribbonExtensibility-Schnittstelle"
  - "Anpassen der Benutzeroberfläche [Office-Entwicklung in Visual Studio]"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Add-Ins auf Anwendungsebene"
  - "Programmierung [Office-Entwicklung in Visual Studio], Add-Ins auf Anwendungsebene"
  - "ThisAddIn-Klasse"
  - "Benutzeroberflächen [Office-Entwicklung in Visual Studio], Anpassen"
  - "Schreiben von Code in Office-Projektmappen"
  - "Hostelemente [Office-Entwicklung in Visual Studio], AddIn"
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Add-Ins auf Anwendungsebene"
  - "Add-Ins [Office-Entwicklung in Visual Studio], ThisAddIn-Klasse"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], ThisAddIn-Klasse"
  - "FormRegionStartup-Schnittstelle"
  - "ThisAddIn_Startup"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Programmierung"
  - "ThisAddIn_Shutdown"
ms.assetid: c534786d-2833-4afa-9e4c-4633f46b9eed
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Programmieren von VSTO-Add-Ins
  Wenn Sie eine Microsoft Office\-Anwendung erweitern, indem Sie ein VSTO\-Add\-In erstellen, schreiben Sie Code direkt für die `ThisAddIn`\-Klasse in Ihrem Projekt. Sie können diese Klasse zum Ausführen von Aufgaben wie das Zugreifen auf das Objektmodell der Microsoft Office\-Hostanwendung, das Anpassen der Benutzeroberfläche \(UI\) einer Anwendung und das Verfügbarmachen von Objekten in Ihrem VSTO\-Add\-In für andere Office\-Projektmappen verwenden.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Einige Aspekte beim Schreiben von Code in VSTO\-Add\-In\-Projekten unterscheiden sich von anderen Projekttypen in Visual Studio. Viele dieser Unterschiede haben mit der Art zu tun, wie die Office\-Objektmodelle im verwalteten Code verfügbar gemacht werden. Weitere Informationen finden Sie unter [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
 Allgemeine Informationen zu VSTO\-Add\-Ins und anderen Arten von Projektmappen, die Sie mit den Office\-Entwicklungstools in Visual Studio erstellen können, finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Verwenden der ThisAddIn\-Klasse  
 Sie können mit dem Schreiben des VSTO\-Add\-In\-Codes in der `ThisAddIn`\-Klasse beginnen. Visual Studio generiert diese Klasse in Ihrem VSTO\-Add\-In\-Projekt automatisch in der Codedatei „ThisAddIn.vb“ \(in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) oder „ThisAddIn.cs“ \(in C\#\). Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instanziiert diese Klasse automatisch für Sie, wenn die Microsoft Office\-Anwendung Ihr VSTO\-Add\-In lädt.  
  
 Es gibt zwei Standardereignishandler in der `ThisAddIn`\-Klasse. Um Code auszuführen, wenn das VSTO\-Add\-In geladen wird, fügen Sie dem `ThisAddIn_Startup`\-Ereignishandler Code hinzu. Um Code direkt vor dem Entladen des VSTO\-Add\-Ins auszuführen, fügen Sie dem `ThisAddIn_Shutdown`\-Ereignishandler Code hinzu. Weitere Informationen zu diesen Ereignishandlern finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  In Outlook wird der `ThisAddIn_Shutdown`\-Ereignishandler standardmäßig nicht jedes Mal aufgerufen, wenn das VSTO\-Add\-In entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
### Zugreifen auf das Objektmodell der Hostanwendung  
 Verwenden Sie zum Zugreifen auf das Objektmodell der Hostanwendung das Feld `Application` der `ThisAddIn`\-Klasse. Dieses Feld gibt ein Objekt zurück, das für die aktuelle Instanz der Hostanwendung steht. In der folgenden Tabelle sind die Typen der Rückgabewerte für das Feld `Application` in jedem VSTO\-Add\-In\-Projekt aufgeführt.  
  
|Hostanwendung|Typ des Rückgabewerts|  
|-------------------|---------------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie das Feld `Application` zum Erstellen einer neuen Arbeitsmappe in einem VSTO\-Add\-In für Microsoft Office Excel verwenden. Dieses Beispiel ist für die Ausführung über die `ThisAddIn`\-Klasse bestimmt.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Verwenden Sie für die Ausführung außerhalb der `ThisAddIn`\-Klasse das `Globals`\-Objekt, um auf die `ThisAddIn`\-Klasse zuzugreifen. Weitere Informationen zum `Globals`\-Objekt finden Sie unter [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office\-Anwendungen finden Sie unter den folgenden Themen:  
  
-   [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)  
  
-   [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)  
  
-   [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath-Projektmappen](../vsto/infopath-solutions.md)  
  
-   [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)  
  
-   [Projektmappen](../vsto/project-solutions.md)  
  
-   [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Zugreifen auf ein Dokument beim Starten der Office\-Anwendung  
 Nicht in allen [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]\-Anwendungen wird ein Dokument automatisch geöffnet, wenn Sie die Anwendung starten, und in keiner [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]\-Anwendung wird ein Dokument geöffnet, wenn Sie sie starten. Fügen Sie dem `ThisAdd-In_Startup`\-Ereignishandler daher keinen Code hinzu, wenn für den Code ein geöffnetes Dokument erforderlich ist. Fügen Sie den Code stattdessen einem Ereignis hinzu, das von der Office\-Anwendung ausgelöst wird, wenn ein Benutzer ein Dokument erstellt oder öffnet. So können Sie sicherstellen, dass ein Dokument geöffnet ist, bevor mit Ihrem Code Schritte dafür ausgeführt werden.  
  
 Das folgende Codebeispiel funktioniert mit einem Word\-Dokument nur dann, wenn der Benutzer ein Dokument erstellt oder ein bestehendes öffnet.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#3)]  
  
### ThisAddIn\-Member für andere Aufgaben  
 In der folgende Tabelle werden weitere häufig vorkommende Aufgaben beschrieben, und es wird gezeigt, welche Member der `ThisAddIn`\-Klasse Sie zum Ausführen der Aufgaben verwenden können.  
  
|Aufgabe|Zu verwendender Member|  
|-------------|----------------------------|  
|Führen Sie Code aus, um das VSTO\-Add\-In zu initialisieren, wenn es geladen wird.|Fügen Sie der `ThisAddIn_Startup`\-Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Startup>\-Ereignis. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).|  
|Führen Sie Code zum Bereinigen von Ressourcen aus, die vom VSTO\-Add\-In verwendet werden, bevor das VSTO\-Add\-In entladen wird.|Fügen Sie der `ThisAddIn_Shutdown`\-Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Shutdown>\-Ereignis. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md). **Note:**  In Outlook wird der `ThisAddIn_Startup`\-Ereignishandler standardmäßig nicht jedes Mal aufgerufen, wenn das VSTO\-Add\-In entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).|  
|Zeigen Sie einen benutzerdefinierten Aufgabenbereich an.|Verwenden Sie das Feld `CustomTaskPanes`. Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).|  
|Machen Sie Objekte im VSTO\-Add\-In für andere Microsoft Office\-Projektmappen verfügbar.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>\-Methode. Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Passen Sie eine Funktion im Microsoft Office System an, indem Sie eine Erweiterbarkeitsschnittstelle implementieren.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A>\-Methode , um eine Instanz einer Klasse zurückzugeben, die die Schnittstelle implementiert. Weitere Informationen finden Sie unter [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Note:**  Zum Anpassen der Menüband\-Benutzeroberfläche können Sie auch die <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A>\-Methode außer Kraft setzen.|  
  
### Grundlegendes zum Entwurf der ThisAddIn\-Klasse  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ausgerichtet sind, ist <xref:Microsoft.Office.Tools.AddIn> eine Schnittstelle. Die `ThisAddIn`\-Klasse wird aus der <xref:Microsoft.Office.Tools.AddInBase>\-Klasse abgeleitet. Diese Basisklasse leitet alle Aufrufe ihrer Member an eine interne Implementierung der <xref:Microsoft.Office.Tools.AddIn>\-Schnittstelle in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] um.  
  
 In VSTO\-Add\-In\-Projekten für Outlook wird die `ThisAddIn`\-Klasse in Projekten mit .NET Framework 3.5 von der Microsoft.Office.Tools.Outlook.OutlookAddIn\-Klasse abgeleitet. In Projekten mit [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] wird sie von <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> abgeleitet. Diese Basisklassen stellen einige zusätzliche Funktionen zur Unterstützung von Formularbereichen bereit. Weitere Informationen zu Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
## Anpassen der Benutzeroberfläche von Microsoft Office\-Anwendungen  
 Sie können die Benutzeroberfläche von Microsoft Office\-Anwendungen programmgesteuert anpassen, indem Sie ein VSTO\-Add\-In verwenden. Beispielsweise können Sie das Menüband anpassen, einen benutzerdefinierten Aufgabenbereich anzeigen oder in Outlook einen benutzerdefinierten Formularbereich erstellen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Visual Studio stellt Designer und Klassen bereit, die Sie zum Erstellen von benutzerdefinierten Aufgabenbereichen, Menübandanpassungen und Outlook\-Formularbereichen verwenden können. Diese Designer und Klassen vereinfachen das Anpassen dieser Funktionen. Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md), [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md) und [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
 Wenn Sie eine dieser Funktionen auf eine Weise anpassen möchten, die von den Klassen und Designern nicht unterstützt wird, können Sie diese Funktionen auch anpassen, indem Sie in Ihrem VSTO\-Add\-In eine *Erweiterbarkeitsschnittstelle* implementieren. Weitere Informationen finden Sie unter [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Darüber hinaus können Sie die Benutzeroberfläche von Word\-Dokumenten und Excel\-Arbeitsmappen ändern, indem Sie Hostelemente generieren, mit denen das Verhalten von Dokumenten und Arbeitsmappen erweitert wird. Dies ermöglicht Ihnen das Hinzufügen von verwalteten Steuerelementen zu Dokumenten und Arbeitsblättern. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Aufrufen von Code in VSTO\-Add\-Ins aus anderen Projektmappen  
 Sie können Objekte in Ihrem VSTO\-Add\-In für andere Projektmappen verfügbar machen, z. B. andere Office\-Projektmappen. Dies ist hilfreich, wenn Ihr VSTO\-Add\-In einen Dienst bereitstellt, der durch andere Projektmappen verwendet werden soll. Wenn Sie beispielsweise über ein VSTO\-Add\-In für Microsoft Office Excel verfügen, das Berechnungen in Bezug auf finanzielle Daten von einem Webdienst vornimmt, können andere Projektmappen diese Berechnungen ausführen, indem sie ein VSTO\-Add\-In für Excel zur Laufzeit aufrufen.  
  
 Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  