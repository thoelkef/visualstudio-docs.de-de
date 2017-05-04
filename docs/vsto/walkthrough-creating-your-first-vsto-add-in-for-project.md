---
title: "Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins f&#252;r Project | Microsoft Docs"
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
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erstellen Ihres ersten Projekts"
  - "Office-Entwicklung in Visual Studio, Erstellen Ihres ersten Projekts"
  - "Project [Office-Entwicklung in Visual Studio], Erstellen Ihres ersten Projekts"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Erstellen Ihres ersten Projekts"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins f&#252;r Project
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie ein VSTO\-Add\-In für Microsoft Office Project erstellen. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Projekte geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines VSTO\-Add\-In\-Projekts für Project.  
  
-   Schreiben von Code, der das Objektmodell von Project verwendet, um eine Aufgabe zu einem neuen Projekt hinzuzufügen.  
  
-   Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.  
  
-   Bereinigen des abgeschlossenen Projekts, damit das VSTO\-Add\-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] oder [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## Erstellen des Projekts  
  
#### So erstellen Sie ein neues Projekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder **Visual Basic** und dann **Office\/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office\/SharePoint** den Knoten **Office\-Add\-Ins** aus.  
  
5.  Wählen Sie in der Liste mit den Projektvorlagen **Project 2010\-Add\-In** oder **Project 2013\-Add\-In** aus.  
  
6.  Geben Sie im Feld **Name** den Text **FirstProjectAddIn** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstProjectAddIn**\-Projekt und öffnet die Codedatei **ThisAddIn** im Editor.  
  
## Schreiben von Code, der einem Projekt eine neue Aufgabe hinzufügt  
 Als Nächstes fügen Sie der Codedatei „ThisAddIn“ Code hinzu. Der neue Code verwendet das Objektmodell von Project, um eine neue Aufgabe zu einem Projekt hinzuzufügen. Standardmäßig enthält die Codedatei „ThisAddIn“ den folgenden generierten Code:  
  
-   Eine Teildefinition der `ThisAddIn`\-Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Project. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md). Der Rest der `ThisAddIn`\-Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown`. Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO\-Add\-In von Project geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO\-Add\-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO\-Add\-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
#### So fügen Sie eine Aufgabe zu einem neuen Projekt hinzu  
  
1.  Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn`\-Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das NewProject\-Ereignis der Microsoft.Office.Interop.MSProject.Application\-Klasse.  
  
     Wenn der Benutzer ein neues Projekt erstellt, fügt dieser Ereignishandler eine Aufgabe zum Projekt hinzu.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 In diesem Codebeispiel werden die folgenden Objekte verwendet, um das Projekt zu ändern:  
  
-   Das Feld `Application` der `ThisAddIn`\-Klasse. Das `Application`\-Feld gibt ein Microsoft.Office.Interop.MSProject.Application\-Objekt zurück, das für die aktuelle Instanz von Project steht.  
  
-   Der Parameter `pj` des Ereignishandlers für das NewProject\-Ereignis. Der `pj`\-Parameter ist ein Microsoft.Office.Interop.MSProject.Project\-Objekt, das das Projekt darstellt. Weitere Informationen finden Sie unter [Projektmappen](../vsto/project-solutions.md).  
  
1.  Wenn Sie C\# verwenden, fügen Sie dem `ThisAddIn_Startup`\-Ereignishandler den folgenden Code hinzu. Dieser Code verbindet den `Application_Newproject`\-Ereignishandler mit dem NewProject\-Ereignis.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## Testen des Projekts  
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass die neue Aufgabe in dem sich ergebenden neuen Projekt angezeigt wird.  
  
#### So testen Sie das Projekt  
  
1.  Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen. Microsoft Project startet und öffnet automatisch ein neues leeres Projekt.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Project das VSTO\-Add\-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO\-Add\-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Übersicht über das Erstellen von Office\-Projektmappen](http://msdn.microsoft.com/de-de/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Stellen Sie sicher, dass dem leeren Projekt eine neue Aufgabe hinzugefügt wird.  
  
3.  Stellen Sie sicher, dass der folgende Text im Feld **Aufgabenname** der Aufgabe angezeigte.  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
4.  Schließen Sie Microsoft Project.  
  
## Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO\-Add\-In\-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO\-Add\-In jedes Mal ausgeführt, wenn Sie Microsoft Project auf dem Entwicklungscomputer öffnen.  
  
#### So bereinigen Sie das Projekt  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## Nächste Schritte  
 Nachdem Sie nun ein einfaches VSTO\-Add\-In für Project erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO\-Add\-Ins erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in VSTO\-Add\-Ins für Project ausführen können: [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Verwenden des Project\-Objektmodells: [Projektmappen](../vsto/project-solutions.md).  
  
-   Erstellen und Debuggen von VSTO\-Add\-Ins für Project: [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von VSTO\-Add\-Ins für Project: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Projektmappen](../vsto/project-solutions.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  