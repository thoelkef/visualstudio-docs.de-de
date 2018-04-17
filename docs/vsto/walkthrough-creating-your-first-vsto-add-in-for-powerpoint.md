---
title: 'Exemplarische Vorgehensweise: Erstellen Ihrer ersten VSTO-Add-Ins für PowerPoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5814262d68d9bf32ee3a0f72e3e0a15811a75a9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-powerpoint"></a>Exemplarische Vorgehensweise: Erstellen eines ersten VSTO-Add-Ins für PowerPoint
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie ein VSTO-Add-In für Microsoft Office PowerPoint erstellen. Die Funktionen, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Präsentationen geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines PowerPoint-VSTO-Add-In-Projekts für PowerPoint  
  
-   Schreiben von Code, der das PowerPoint-Objektmodell verwendet, um jeder neuen Folie ein Textfeld hinzuzufügen  
  
-   Erstellen und Ausführen des Projekts, um es zu testen  
  
-   Bereinigen des Projekts, sodass das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein PowerPoint-VSTO-Add-In-Projekt aus.  
  
6.  In der **Namen** geben **FirstPowerPointAddIn**.  
  
7.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt die **FirstPowerPointAddIn** -Projekt und öffnet die **"ThisAddIn"** Codedatei im Editor.  
  
## <a name="writing-code-that-adds-text-to-each-new-slide"></a>Schreiben von Code, der jeder neuen Folie Text hinzufügt  
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code, verwendet das PowerPoint-Objektmodell, um jeder neuen Folie ein Textfeld hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:  
  
-   Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von PowerPoint. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Der Rest der `ThisAddIn` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von PowerPoint geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-text-box-to-each-new-slide"></a>So fügen Sie jeder neuen Folie ein Textfeld hinzu  
  
1.  Fügen Sie in der Codedatei "ThisAddIn" der `ThisAddIn`-Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>-Ereignis des <xref:Microsoft.Office.Interop.PowerPoint.Application>-Objekts.  
  
     Wenn der Benutzer der aktiven Präsentation eine neue Folie hinzufügt, fügt dieser Ereignishandler oben auf der neuen Folie ein Textfeld hinzu und fügt Text in das Textfeld ein.  
  
     [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden Code hinzu. Dieser Code ist erforderlich, um den `Application_PresentationNewSlide`-Ereignishandler mit dem <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>-Ereignis zu verbinden.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
 Zum Ändern der einzelnen neuen Folien wurden in den vorherigen Codebeispielen die folgenden Objekte verwendet:  
  
-   Das `Application`-Feld der `ThisAddIn`-Klasse. Das `Application`-Feld gibt ein <xref:Microsoft.Office.Interop.PowerPoint.Application>-Objekt zurück, das für die aktuelle Instanz von PowerPoint steht.  
  
-   Der Parameter `Sld` des Ereignishandlers für das <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>-Ereignis. Der `Sld`-Parameter ist ein <xref:Microsoft.Office.Interop.PowerPoint.Slide>-Objekt, das die neue Folie darstellt. Weitere Informationen finden Sie unter [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md).  
  
## <a name="testing-the-project"></a>Testen des Projekts  
 Überprüfen Sie, wenn Sie das Projekt erstellen und ausführen, ob in neuen Folien, die Sie einer Präsentation hinzufügen, das Textfeld angezeigt wird.  
  
#### <a name="to-test-the-project"></a>So testen Sie das Projekt  
  
1.  Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die in den Buildausgabeordner des Projekts eingefügt wird. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe PowerPoint das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Fügen Sie in PowerPoint der aktiven Präsentation eine neue Folie hinzu.  
  
3.  Stellen Sie sicher, dass einem neuen Textfeld am oberen Rand der Folie der folgende Text hinzugefügt wird.  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
4.  Schließen Sie PowerPoint.  
  
## <a name="cleaning-up-the-project"></a>Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie PowerPoint auf dem Entwicklungscomputer öffnen.  
  
#### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem Sie nun ein einfaches VSTO-Add-In für PowerPoint erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins für PowerPoint ausführen können. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Verwenden des Objektmodells von PowerPoint. Weitere Informationen finden Sie unter [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md).  
  
-   Anpassen der Benutzeroberfläche (UI) von PowerPoint beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Erstellen und Debuggen von VSTO-Add-Ins für PowerPoint. Weitere Informationen finden Sie unter [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von VSTO-Add-Ins für PowerPoint. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  