---
title: Programmieren von VSTO-Add-ins
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b9b809750e658b6a5e496e2d90b7b396157f87a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079011"
---
# <a name="program-vsto-add-ins"></a>Programmieren von VSTO-Add-ins
  Wenn Sie eine Microsoft Office-Anwendung erweitern, indem Sie ein VSTO-Add-In erstellen, schreiben Sie Code direkt für die `ThisAddIn` -Klasse in Ihrem Projekt. Sie können diese Klasse zum Ausführen von Aufgaben wie das Zugreifen auf das Objektmodell der Microsoft Office-Hostanwendung, das Anpassen der Benutzeroberfläche (UI) einer Anwendung und das Verfügbarmachen von Objekten in Ihrem VSTO-Add-In für andere Office-Projektmappen verwenden.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Einige Aspekte beim Schreiben von Code in VSTO-Add-In-Projekten unterscheiden sich von anderen Projekttypen in Visual Studio. Viele dieser Unterschiede haben mit der Art zu tun, wie die Office-Objektmodelle im verwalteten Code verfügbar gemacht werden. Weitere Informationen finden Sie unter [schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).

 Allgemeine Informationen zu VSTO-Add-ins und anderen Typen von Projektmappen, die Sie mithilfe von Office-Entwicklungstools in Visual Studio erstellen können, finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Verwenden der ThisAddIn-Klasse
 Sie können mit dem Schreiben des VSTO-Add-In-Codes in der `ThisAddIn` -Klasse beginnen. Visual Studio automatisch generiert diese Klasse in der *"ThisAddIn.vb"* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) oder *"ThisAddIn.cs"* (in c#) code-Datei in Ihrem VSTO-Add-in-Projekt. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instanziiert diese Klasse automatisch für Sie, wenn die Microsoft Office-Anwendung Ihr VSTO-Add-In lädt.

 Es gibt zwei Standardereignishandler in der `ThisAddIn` -Klasse. Um Code auszuführen, wenn das VSTO-Add-In geladen wird, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler Code hinzu. Um Code direkt vor dem Entladen des VSTO-Add-Ins auszuführen, fügen Sie dem `ThisAddIn_Shutdown` -Ereignishandler Code hinzu. Weitere Informationen zu diesen Ereignishandlern finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

> [!NOTE]
>  In Outlook wird der `ThisAddIn_Shutdown` -Ereignishandler standardmäßig nicht jedes Mal aufgerufen, wenn das VSTO-Add-In entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Zugriff auf das Objektmodell der hostanwendung
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

 Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit der `Application` Feld, um eine neue Arbeitsmappe in einem VSTO-Add-in für Microsoft Office Excel zu erstellen. Dieses Beispiel ist für die Ausführung über die `ThisAddIn` -Klasse bestimmt.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Verwenden Sie für die Ausführung außerhalb der `ThisAddIn` -Klasse das `Globals` -Objekt, um auf die `ThisAddIn` -Klasse zuzugreifen. Weitere Informationen zu den `Globals` Objekt, finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office-Anwendungen finden Sie unter den folgenden Themen:

- [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md)

- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)

- [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)

- [InfoPath-Lösungen](../vsto/infopath-solutions.md)

- [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)

- [Projektmappen](../vsto/project-solutions.md)

- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)

### <a name="AccessingDocuments"></a> Auf zugreifen Sie ein Dokument, beim Starten der Office-Anwendung
 Nicht in allen [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] -Anwendungen wird ein Dokument automatisch geöffnet, wenn Sie die Anwendung starten, und in keiner [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Anwendung wird ein Dokument geöffnet, wenn Sie sie starten. Aus diesem Grund nicht fügen Sie Code in die `ThisAdd-In_Startup` -Ereignishandler, wenn der Code ein geöffnetes Dokument erforderlich ist. Fügen Sie stattdessen diesen Code einem Ereignis hinzu, welches durch die Office-Anwendung ausgelöst wird, wenn vom Benutzer ein Dokument erstellt oder geöffnet wird. So können Sie sicherstellen, dass ein Dokument geöffnet ist, bevor mit Ihrem Code Schritte dafür ausgeführt werden.

 Das folgende Codebeispiel funktioniert mit einem Word-Dokument nur dann, wenn der Benutzer ein Dokument erstellt oder ein bestehendes öffnet.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn-Member für andere Aufgaben verwenden.
 In der folgende Tabelle werden weitere häufig vorkommende Aufgaben beschrieben, und es wird gezeigt, welche Member der `ThisAddIn` -Klasse Sie zum Ausführen der Aufgaben verwenden können.

|Aufgabe|Zu verwendender Member|
|----------|-------------------|
|Führen Sie Code aus, um das VSTO-Add-In zu initialisieren, wenn es geladen wird.|Fügen Sie der `ThisAddIn_Startup` -Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Startup> -Ereignis. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).|
|Führen Sie Code zum Bereinigen von Ressourcen aus, die vom VSTO-Add-In verwendet werden, bevor das VSTO-Add-In entladen wird.|Fügen Sie der `ThisAddIn_Shutdown` -Methode Code hinzu. Dies ist der Standardereignishandler für das <xref:Microsoft.Office.Tools.AddInBase.Shutdown> -Ereignis. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md). **Hinweis**:  In Outlook wird der `ThisAddIn_Startup` -Ereignishandler standardmäßig nicht jedes Mal aufgerufen, wenn das VSTO-Add-In entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).|
|Zeigen Sie einen benutzerdefinierten Aufgabenbereich an.|Verwenden Sie das Feld `CustomTaskPanes` . Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).|
|Machen Sie Objekte im VSTO-Add-In für andere Microsoft Office-Projektmappen verfügbar.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>-Methode. Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Passen Sie eine Funktion im Microsoft Office System an, indem Sie eine Erweiterbarkeitsschnittstelle implementieren.|Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> -Methode , um eine Instanz einer Klasse zurückzugeben, die die Schnittstelle implementiert. Weitere Informationen finden Sie unter [Anpassen der UI-Features mithilfe von Erweiterbarkeitsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Hinweis**:  Zum Anpassen der Menüband-Benutzeroberfläche können Sie auch die <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A>-Methode außer Kraft setzen.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Verstehen des Systementwurfs der ThisAddIn-Klasse
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet sind, ist <xref:Microsoft.Office.Tools.AddIn> eine Schnittstelle. Die `ThisAddIn` -Klasse wird aus der <xref:Microsoft.Office.Tools.AddInBase> -Klasse abgeleitet. Diese Basisklasse leitet alle Aufrufe ihrer Member an eine interne Implementierung der <xref:Microsoft.Office.Tools.AddIn> -Schnittstelle in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]um.

 In VSTO-Add-In-Projekten für Outlook wird die `ThisAddIn`-Klasse in Projekten mit .NET Framework 3.5 von der `Microsoft.Office.Tools.Outlook.OutlookAddIn`-Klasse abgeleitet. In Projekten mit [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] wird sie von <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> abgeleitet. Diese Basisklassen stellen einige zusätzliche Funktionen zur Unterstützung von Formularbereichen bereit. Weitere Informationen zu Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Anpassen der Benutzeroberfläche von Microsoft Office-Anwendungen
 Sie können die Benutzeroberfläche von Microsoft Office-Anwendungen programmgesteuert anpassen, indem Sie ein VSTO-Add-In verwenden. Beispielsweise können Sie das Menüband anpassen, einen benutzerdefinierten Aufgabenbereich anzeigen oder in Outlook einen benutzerdefinierten Formularbereich erstellen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

 Visual Studio stellt Designer und Klassen bereit, die Sie zum Erstellen von benutzerdefinierten Aufgabenbereichen, Menübandanpassungen und Outlook-Formularbereichen verwenden können. Diese Designer und Klassen vereinfachen das Anpassen dieser Funktionen. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md), [Menüband-Designer](../vsto/ribbon-designer.md), und [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).

 Wenn Sie eine dieser Funktionen auf eine Weise anpassen möchten, die von den Klassen und Designern nicht unterstützt wird, können Sie diese Funktionen auch anpassen, indem Sie in Ihrem VSTO-Add-In eine *Erweiterbarkeitsschnittstelle* implementieren. Weitere Informationen finden Sie unter [Anpassen der UI-Features mithilfe von Erweiterbarkeitsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Darüber hinaus können Sie die Benutzeroberfläche von Word-Dokumenten und Excel-Arbeitsmappen ändern, indem Sie Hostelemente generieren, mit denen das Verhalten von Dokumenten und Arbeitsmappen erweitert wird. Dies ermöglicht Ihnen das Hinzufügen von verwalteten Steuerelementen zu Dokumenten und Arbeitsblättern. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Aufrufen von Code in VSTO-Add-ins aus anderen Projektmappen
 Sie können Objekte in Ihrem VSTO-Add-In für andere Projektmappen verfügbar machen, z. B. andere Office-Projektmappen. Dies ist hilfreich, wenn Ihr VSTO-Add-In einen Dienst bereitstellt, der durch andere Projektmappen verwendet werden soll. Z. B. Wenn Sie ein VSTO-Add-in für Microsoft Office Excel, die Berechnungen auf finanzielle Daten von einem Webdienst vornimmt verfügen, können andere Projektmappen diese Berechnungen durch den Aufruf in das Excel-VSTO-Add-in zur Laufzeit ausführen.

 Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Siehe auch
- [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Anpassen von Funktionen der Benutzeroberfläche mithilfe von Erweiterbarkeitsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
