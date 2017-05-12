---
title: "Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins f&#252;r Outlook"
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
  - "Add-Ins [Office-Entwicklung in Visual Studio], Erstellen Ihres ersten Projekts"
  - "Outlook [Office-Entwicklung in Visual Studio], Erstellen Ihres ersten Projekts"
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins f&#252;r Outlook
  Diese exemplarische Vorgehensweise veranschaulicht die Erstellung eines VSTO\-Add\-Ins für Microsoft Office Outlook. Die in dieser Art von Projektmappe erstellten Features sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welches Outlook\-Element geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines VSTO\-Add\-In\-Projekts für Outlook  
  
-   Schreiben von Code, der das Outlook\-Objektmodell verwendet, um der Betreffzeile und dem Textkörper einer neuen E\-Mail Text hinzuzufügen  
  
-   Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.  
  
-   Bereinigen des abgeschlossenen Projekts, damit das VSTO\-Add\-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Erstellen des Projekts  
  
#### So erstellen Sie ein neues Outlook\-Projekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder **Visual Basic** und dann **Office\/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office\/SharePoint** den Knoten **Office\-Add\-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein Outlook\-VSTO\-Add\-In\-Projekt aus.  
  
6.  Geben Sie im Feld **Name** den Text **FirstOutlookAddIn** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstOutlookAddIn**\-Projekt und öffnet die Codedatei **ThisAddIn** im Editor.  
  
## Schreiben von Code, durch den jeder neuen E\-Mail Text hinzugefügt wird  
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Outlook\-Objektmodell, um jeder neuen E\-Mail Text hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:  
  
-   Eine Teildefinition der `ThisAddIn`\-Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Outlook\-Objektmodell. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md). Der Rest der `ThisAddIn`\-Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown`. Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO\-Add\-In von Outlook geladen oder entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO\-Add\-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO\-Add\-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
#### So fügen Sie der Betreffzeile und dem Textkörper jeder neuen E\-Mail Text hinzu  
  
1.  Deklarieren Sie in der ThisAddIn\-Codedatei ein Feld namens `inspectors` in der `ThisAddIn`\-Klasse. Das`inspectors`\-Feld behält einen Verweis auf die Auflistung von Inspektor\-Fenstern in der aktuellen Outlook\-Instanz. Dieser Verweis verhindert, dass der Garbage Collector den Speicher freigibt, der den Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis enthält.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_OutlookAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Ersetzen Sie die `ThisAddIn_Startup`\-Methode durch folgenden Code: Dieser Code fügt einen Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis an.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookAddInTutorial#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#2)]  
  
3.  Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn`\-Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis.  
  
     Wenn der Benutzer eine neue E\-Mail erstellt, fügt dieser Ereignishandler der Betreffzeile und dem Textkörper der Nachricht Text hinzu.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookAddInTutorial#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#3)]  
  
 Zum Ändern der einzelnen neuen E\-Mails werden in den vorherigen Codebeispielen die folgenden Objekte verwendet:  
  
-   Das `Application`\-Feld der `ThisAddIn`\-Klasse. Das `Application`\-Feld gibt ein <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekt zurück, das für die aktuelle Instanz von Outlook steht.  
  
-   Der `Inspector`\-Parameter des Ereignishandlers für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis. Der `Inspector`\-Parameter ist ein <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt, das das Inspektorfenster der neuen E\-Mail darstellt. Weitere Informationen finden Sie unter [Outlook-Projektmappen](../vsto/outlook-solutions.md).  
  
## Testen des Projekts  
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass der Text in der Betreffzeile und dem Textkörper der neuen E\-Mail angezeigt wird.  
  
#### So testen Sie das Projekt  
  
1.  Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Outlook das VSTO\-Add\-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO\-Add\-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Office Solution Build Process Overview](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  Erstellen Sie in Outlook eine neue E\-Mail.  
  
3.  Stellen Sie sicher, dass der folgende Text sowohl der Betreffzeile als auch dem Textkörper der Nachricht hinzugefügt wird.  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
4.  Schließen Sie Outlook.  
  
## Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO\-Add\-In\-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO\-Add\-In jedes Mal ausgeführt, wenn Sie Outlook auf dem Entwicklungscomputer öffnen.  
  
#### So bereinigen Sie das Projekt  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## Nächste Schritte  
 Nachdem Sie nun ein einfaches VSTO\-Add\-In für Outlook erstellt haben, erfahren Sie in den folgenden Themen mehr über die Entwicklung von VSTO\-Add\-Ins:  
  
-   Allgemeine Programmieraufgaben, die Sie ausführen können, indem Sie VSTO\-Add\-Ins für Outlook verwenden. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Verwenden des Outlook\-Objektmodells. Weitere Informationen finden Sie unter [Outlook-Projektmappen](../vsto/outlook-solutions.md).  
  
-   Anpassen der Outlook\-Benutzeroberfläche \(UI\) beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Erstellen und Debuggen von VSTO\-Add\-Ins für Outlook. Weitere Informationen finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von VSTO\-Add\-Ins für Outlook. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Outlook-Projektmappen](../vsto/outlook-solutions.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  