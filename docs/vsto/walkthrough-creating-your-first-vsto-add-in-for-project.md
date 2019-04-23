---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d257953aeefd56a8b58a75377a64a5d9e882a25
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665206"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines VSTO-Add-Ins für Microsoft Office-Projekt. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Projekte geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines VSTO-Add-In-Projekts für Project.

- Schreiben von Code, der das Objektmodell von Project verwendet, um eine Aufgabe zu einem neuen Projekt hinzuzufügen.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] oder [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen eines Projekts

### <a name="to-create-a-new-project-in-visual-studio"></a>So erstellen Sie ein neues Projekt in Visual Studio

1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3.  Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.

4.  Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5.  Wählen Sie in der Liste mit den Projektvorlagen **Project 2010-Add-In** oder **Project 2013-Add-In**aus.

6.  Geben Sie im Feld **Name** den Text **FirstProjectAddIn**ein.

7.  Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstProjectAddIn** -Projekt und öffnet die Codedatei **ThisAddIn** im Editor.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Schreiben von Code, der ein Projekt eine neue Aufgabe hinzufügt
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Objektmodell von Project, um eine neue Aufgabe zu einem Projekt hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

-   Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Project. Weitere Informationen finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der `ThisAddIn` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.

-   Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Project geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>So fügen Sie eine Aufgabe zu einem neuen Projekt hinzu

1. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das `NewProject`-Ereignis der `Microsoft.Office.Interop.MSProject.Application`-Klasse.

    Wenn der Benutzer ein neues Projekt erstellt, fügt dieser Ereignishandler eine Aufgabe zum Projekt hinzu.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   Um das Projekt zu ändern, wird in diesem Codebeispiel wird die folgenden Objekte verwendet:

-   Das `Application` -Feld der `ThisAddIn` -Klasse. Das `Application`-Feld gibt ein `Microsoft.Office.Interop.MSProject.Application`-Objekt zurück, das für die aktuelle Instanz von Project steht.

-   Die `pj` Parameter des ereignishandlers für das NewProject-Ereignis. Der `pj`-Parameter ist ein `Microsoft.Office.Interop.MSProject.Project`-Objekt, das das Projekt darstellt. Weitere Informationen finden Sie unter [Projekt Lösungen](../vsto/project-solutions.md).

1.  Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden Code hinzu. Dieser Code verbindet den `Application_Newproject` -Ereignishandler mit dem NewProject-Ereignis.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Testen Sie das Projekt
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass die neue Aufgabe in dem sich ergebenden neuen Projekt angezeigt wird.

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1.  Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen. Microsoft Project startet und öffnet automatisch ein neues leeres Projekt.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Project das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Übersicht über Office-Lösung das Erstellen](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2.  Stellen Sie sicher, dass dem leeren Projekt eine neue Aufgabe hinzugefügt wird.

3.  Stellen Sie sicher, dass der folgende Text im Feld **Aufgabenname** der Aufgabe angezeigte.

     **Dieser Text wurde per Code hinzugefügt.**

4.  Schließen Sie Microsoft Project.

## <a name="clean-up-the-project"></a>Bereinigen Sie das Projekt
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie Microsoft Project auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt

1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für Project erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:

-   Allgemeine Programmieraufgaben, die Sie in VSTO-Add-ins für Project ausführen können: [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

-   Verwenden das Objektmodell von Project: [Projekt Lösungen](../vsto/project-solutions.md).

-   Erstellen und Debuggen von VSTO-Add-ins für Project: [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).

-   Bereitstellen von VSTO-Add-ins für Project: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Siehe auch
- [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Projektmappen](../vsto/project-solutions.md)
- [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
