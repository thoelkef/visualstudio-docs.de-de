---
title: Programmieren von VSTO-Add-Ins | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
ms.assetid: c534786d-2833-4afa-9e4c-4633f46b9eed
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0dfc26627bbeaaaea66fb942e87238814bd02fd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="programming-vsto-add-ins"></a>Programmieren von VSTO-Add-Ins
  Wenn Sie eine Microsoft Office-Anwendung erweitern, indem Sie ein VSTO-Add-In erstellen, schreiben Sie Code direkt für die `ThisAddIn` -Klasse in Ihrem Projekt. Sie können diese Klasse zum Ausführen von Aufgaben wie das Zugreifen auf das Objektmodell der Microsoft Office-Hostanwendung, das Anpassen der Benutzeroberfläche (UI) einer Anwendung und das Verfügbarmachen von Objekten in Ihrem VSTO-Add-In für andere Office-Projektmappen verwenden.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Einige Aspekte beim Schreiben von Code in VSTO-Add-In-Projekten unterscheiden sich von anderen Projekttypen in Visual Studio. Viele dieser Unterschiede haben mit der Art zu tun, wie die Office-Objektmodelle im verwalteten Code verfügbar gemacht werden. Weitere Informationen finden Sie unter [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
 Allgemeine Informationen zu VSTO-Add-ins und anderen Arten von Projektmappen, die Sie mithilfe der Office-Entwicklungstools in Visual Studio erstellen können, finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-thisaddin-class"></a>Verwenden der ThisAddIn-Klasse  
 Sie können mit dem Schreiben des VSTO-Add-In-Codes in der `ThisAddIn` -Klasse beginnen. Visual Studio generiert diese Klasse in Ihrem VSTO-Add-In-Projekt automatisch in der Codedatei „ThisAddIn.vb“ (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) oder „ThisAddIn.cs“ (in C#). Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instanziiert diese Klasse automatisch für Sie, wenn die Microsoft Office-Anwendung Ihr VSTO-Add-In lädt.  
  
 Es gibt zwei Standardereignishandler in der `ThisAddIn` -Klasse. Um Code auszuführen, wenn das VSTO-Add-In geladen wird, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler Code hinzu. Um Code direkt vor dem Entladen des VSTO-Add-Ins auszuführen, fügen Sie dem `ThisAddIn_Shutdown` -Ereignishandler Code hinzu. Weitere Informationen zu diesen Ereignishandlern finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  In Outlook wird der `ThisAddIn_Shutdown` -Ereignishandler standardmäßig nicht jedes Mal aufgerufen, wenn das VSTO-Add-In entladen wird. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-object-model-of-the-host-application"></a>Zugreifen auf das Objektmodell der Hostanwendung  
 Verwenden Sie zum Zugreifen auf das Objektmodell der Hostanwendung das Feld `Application` der `ThisAddIn` -Klasse. Dieses Feld gibt ein Objekt zurück, das für die aktuelle Instanz der Hostanwendung steht. In der folgenden Tabelle sind die Typen der Rückgabewerte für das Feld `Application` in jedem VSTO-Add-In-Projekt aufgeführt.  
  
|Hostanwendung|Typ des Rückgabewerts|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie das Feld `Application` zum Erstellen einer neuen Arbeitsmappe in einem VSTO-Add-In für Microsoft Office Excel verwenden. Dieses Beispiel ist für die Ausführung über die `ThisAddIn` -Klasse bestimmt.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Verwenden Sie für die Ausführung außerhalb der `ThisAddIn` -Klasse das `Globals` -Objekt, um auf die `ThisAddIn` -Klasse zuzugreifen. Weitere Informationen zu den `Globals` Objekt, finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office-Anwendungen finden Sie unter den folgenden Themen:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath-Projektmappen](../vsto/infopath-solutions.md)  
  
-   [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)  
  
-   [Project-Projektmappen](../vsto/project-solutions.md)  
  
-   [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Zugreifen auf ein Dokument beim Starten der Office-Anwendung  
 Nicht in allen [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] -Anwendungen wird ein Dokument automatisch geöffnet, wenn Sie die Anwendung starten, und in keiner [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Anwendung wird ein Dokument geöffnet, wenn Sie sie starten. Aus diesem Grund nicht fügen Sie Code in die `ThisAdd-In_Startup` Ereignishandler, wenn der Code ein geöffnetes Dokument erforderlich ist. Fügen Sie stattdessen diesen Code einem Ereignis hinzu, welches durch die Office-Anwendung ausgelöst wird, wenn vom Benutzer ein Dokument erstellt oder geöffnet wird. So können Sie sicherstellen, dass ein Dokument geöffnet ist, bevor mit Ihrem Code Schritte dafür ausgeführt werden.  
  
 Das folgende Codebeispiel funktioniert mit einem Word-Dokument nur dann, wenn der Benutzer ein Dokument erstellt oder ein bestehendes öffnet.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn-Member für andere Aufgaben  
 In der folgende Tabelle werden weitere häufig vorkommende Aufgaben beschrieben, und es wird gezeigt, welche Member der `ThisAddIn` -Klasse Sie zum Ausführen der Aufgaben verwenden können.  
  
|Aufgabe|Zu verwendender Member|  
|----------|-------------------|  
|Führen Sie Code aus, um das VSTO-Add-In zu initialisieren, wenn es geladen wird.|Fügen Sie der `ThisAddIn_Startup` -Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Startup> -Ereignis. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).|  
|Führen Sie Code zum Bereinigen von Ressourcen aus, die vom VSTO-Add-In verwendet werden, bevor das VSTO-Add-In entladen wird.|Fügen Sie der `ThisAddIn_Shutdown` -Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Shutdown> -Ereignis. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md). **Hinweis:** In Outlook wird standardmäßig der `ThisAddIn_Startup` -Ereignishandler nicht immer aufgerufen, wenn das VSTO-Add-in entladen wird. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).|  
|Zeigen Sie einen benutzerdefinierten Aufgabenbereich an.|Verwenden Sie das Feld `CustomTaskPanes` . Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).|  
|Machen Sie Objekte im VSTO-Add-In für andere Microsoft Office-Projektmappen verfügbar.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> -Methode. Weitere Informationen finden Sie unter [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Passen Sie eine Funktion im Microsoft Office System an, indem Sie eine Erweiterbarkeitsschnittstelle implementieren.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> -Methode , um eine Instanz einer Klasse zurückzugeben, die die Schnittstelle implementiert. Weitere Informationen finden Sie unter [Customizing UI Features By Using Extensibility Interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Hinweis:** zum Anpassen des Menübands-Benutzeroberfläche können Sie auch überschreiben die <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> Methode.|  
  
### <a name="understanding-the-design-of-the-thisaddin-class"></a>Grundlegendes zum Entwurf der ThisAddIn-Klasse  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet sind, ist <xref:Microsoft.Office.Tools.AddIn> eine Schnittstelle. Die `ThisAddIn` -Klasse wird aus der <xref:Microsoft.Office.Tools.AddInBase> -Klasse abgeleitet. Diese Basisklasse leitet alle Aufrufe ihrer Member an eine interne Implementierung der <xref:Microsoft.Office.Tools.AddIn> -Schnittstelle in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]um.  
  
 In VSTO-Add-in-Projekten für Outlook wird der `ThisAddIn` Klasse abgeleitet wird, von der Klasse Microsoft.Office.Tools.Outlook.OutlookAddIn in Projekten, die auf .NET Framework 3.5 abzielen, und von <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> in Projekten, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Diese Basisklassen stellen einige zusätzliche Funktionen zur Unterstützung von Formularbereichen bereit. Weitere Informationen zu Formularbereichen finden Sie unter [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Anpassen der Benutzeroberfläche von Microsoft Office-Anwendungen  
 Sie können die Benutzeroberfläche von Microsoft Office-Anwendungen programmgesteuert anpassen, indem Sie ein VSTO-Add-In verwenden. Beispielsweise können Sie das Menüband anpassen, einen benutzerdefinierten Aufgabenbereich anzeigen oder in Outlook einen benutzerdefinierten Formularbereich erstellen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Visual Studio stellt Designer und Klassen bereit, die Sie zum Erstellen von benutzerdefinierten Aufgabenbereichen, Menübandanpassungen und Outlook-Formularbereichen verwenden können. Diese Designer und Klassen vereinfachen das Anpassen dieser Funktionen. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md), [Menüband-Designer](../vsto/ribbon-designer.md), und [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
 Wenn Sie eine dieser Funktionen auf eine Weise anpassen möchten, die von den Klassen und Designern nicht unterstützt wird, können Sie diese Funktionen auch anpassen, indem Sie in Ihrem VSTO-Add-In eine *Erweiterbarkeitsschnittstelle* implementieren. Weitere Informationen finden Sie unter [Customizing UI Features By Using Extensibility Interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Darüber hinaus können Sie die Benutzeroberfläche von Word-Dokumenten und Excel-Arbeitsmappen ändern, indem Sie Hostelemente generieren, mit denen das Verhalten von Dokumenten und Arbeitsmappen erweitert wird. Dies ermöglicht Ihnen das Hinzufügen von verwalteten Steuerelementen zu Dokumenten und Arbeitsblättern. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="calling-code-in-vsto-add-ins-from-other-solutions"></a>Aufrufen von Code in VSTO-Add-Ins aus anderen Projektmappen  
 Sie können Objekte in Ihrem VSTO-Add-In für andere Projektmappen verfügbar machen, z. B. andere Office-Projektmappen. Dies ist hilfreich, wenn Ihr VSTO-Add-In einen Dienst bereitstellt, der durch andere Projektmappen verwendet werden soll. Wenn Sie beispielsweise über ein VSTO-Add-In für Microsoft Office Excel verfügen, das Berechnungen in Bezug auf finanzielle Daten von einem Webdienst vornimmt, können andere Projektmappen diese Berechnungen ausführen, indem sie ein VSTO-Add-In für Excel zur Laufzeit aufrufen.  
  
 Weitere Informationen finden Sie unter [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  