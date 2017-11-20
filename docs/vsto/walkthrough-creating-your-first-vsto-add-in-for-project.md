---
title: "Exemplarische Vorgehensweise: Erstellen Ihrer ersten VSTO-Add-Ins für Project | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 324d5e07ed2c1515036282abe12336f90225993f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie ein VSTO-Add-In für Microsoft Office Project erstellen. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Projekte geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines VSTO-Add-In-Projekts für Project.  
  
-   Schreiben von Code, der das Objektmodell von Project verwendet, um eine Aufgabe zu einem neuen Projekt hinzuzufügen.  
  
-   Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.  
  
-   Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] oder [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>So erstellen Sie ein neues Projekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.  
  
5.  Wählen Sie in der Liste mit den Projektvorlagen **Project 2010-Add-In** oder **Project 2013-Add-In**aus.  
  
6.  Geben Sie im Feld **Name** den Text **FirstProjectAddIn**ein.  
  
7.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstProjectAddIn** -Projekt und öffnet die Codedatei **ThisAddIn** im Editor.  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>Schreiben von Code, der einem Projekt eine neue Aufgabe hinzufügt  
 Als Nächstes fügen Sie der Codedatei „ThisAddIn“ Code hinzu. Der neue Code verwendet das Objektmodell von Project, um eine neue Aufgabe zu einem Projekt hinzuzufügen. Standardmäßig enthält die Codedatei „ThisAddIn“ den folgenden generierten Code:  
  
-   Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Project. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Der Rest der `ThisAddIn` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Project geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-task-to-a-new-project"></a>So fügen Sie eine Aufgabe zu einem neuen Projekt hinzu  
  
1.  Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das Ereignis "Neues Projekt" die Microsoft.Office.Interop.MSProject.Application-Klasse.  
  
     Wenn der Benutzer ein neues Projekt erstellt, fügt dieser Ereignishandler eine Aufgabe zum Projekt hinzu.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 In diesem Codebeispiel werden die folgenden Objekte verwendet, um das Projekt zu ändern:  
  
-   Das Feld `Application` der `ThisAddIn` -Klasse. Die `Application` Feld gibt ein Microsoft.Office.Interop.MSProject.Application-Objekt, das die aktuelle Instanz von Project darstellt.  
  
-   Die `pj` Parameter des ereignishandlers für das Ereignis neues Projekt. Die `pj` Parameter ist ein Microsoft.Office.Interop.MSProject.Project-Objekt, das das Projekt darstellt. Weitere Informationen finden Sie unter [Project Solutions](../vsto/project-solutions.md).  
  
1.  Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden Code hinzu. Dieser Code verbindet den `Application_Newproject` -Ereignishandler mit dem Ereignis neues Projekt.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>Testen des Projekts  
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass die neue Aufgabe in dem sich ergebenden neuen Projekt angezeigt wird.  
  
#### <a name="to-test-the-project"></a>So testen Sie das Projekt  
  
1.  Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen. Microsoft Project startet und öffnet automatisch ein neues leeres Projekt.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Project das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Übersicht über das Erstellen von Office-Projektmappen](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Stellen Sie sicher, dass dem leeren Projekt eine neue Aufgabe hinzugefügt wird.  
  
3.  Stellen Sie sicher, dass der folgende Text im Feld **Aufgabenname** der Aufgabe angezeigte.  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
4.  Schließen Sie Microsoft Project.  
  
## <a name="cleaning-up-the-project"></a>Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie Microsoft Project auf dem Entwicklungscomputer öffnen.  
  
#### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem Sie nun ein einfaches VSTO-Add-In für Project erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins für Project ausführen können: [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Verwenden des Project-Objektmodells: [Project Solutions](../vsto/project-solutions.md).  
  
-   Erstellen und Debuggen von VSTO-Add-ins für Project: [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von VSTO-Add-ins für Project: [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Projektmappen](../vsto/project-solutions.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  