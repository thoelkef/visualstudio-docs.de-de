---
title: "Exemplarische Vorgehensweise: Erstellen Ihres ersten VSTO-Add-Ins f&#252;r Word | Microsoft Docs"
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
  - "Add-Ins [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
  - "Office-Entwicklung in Visual Studio, Erstellen eines ersten Projekts"
  - "Word [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
ms.assetid: 9d857be7-5c74-4303-baf4-672afc1ea397
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Exemplarische Vorgehensweise: Erstellen Ihres ersten VSTO-Add-Ins f&#252;r Word
  Diese exemplarischen Vorgehensweise bietet eine Einführung in das Erstellen eines VSTO\-Add\-Ins für Microsoft Office Word.  Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Dokumente geöffnet sind.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines VSTO\-Add\-In\-Projekts.  
  
-   Schreiben von Code, in dem das Word\-Objektmodell zum Hinzufügen von Text zu einem Dokument beim Speichern verwendet wird.  
  
-   Erstellen und Ausführen des Projekts, um es zu testen.  
  
-   Bereinigen des abgeschlossenen Projekts, damit das VSTO\-Add\-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Erstellen des Projekts  
  
#### So erstellen Sie ein neues Word VSTO\-Add\-In\-Projekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder  **Visual Basic** und dann **Office\/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office\/SharePoint** den Knoten **Office\-Add\-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein Word VSTO\-Add\-In\-Projekt aus.  
  
6.  Geben Sie im Feld **Name** den Text **FirstWordAddIn** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt **FirstWordAddIn** und öffnet die Codedatei "ThisAddIn" im Editor.  
  
## Schreiben von Code zum Hinzufügen von Text zum gespeicherten Dokument  
 Fügen Sie der Codedatei "ThisAddIn" nun Code hinzu.  Der neue Code verwendet das Word\-Objektmodell, um jedem gespeicherten einen Textbaustein hinzuzufügen.  Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:  
  
-   Eine Teildefinition der Klasse `ThisAddIn`.  Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Word.  Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  Die restliche Klasse `ThisAddIn` wird in einer ausgeblendeten Codedatei definiert, die Sie nicht ändern sollten.  
  
-   Die `ThisAddIn_Startup`\- und `ThisAddIn_Shutdown`\-Ereignishandler.  Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO\-Add\-In von Word geladen und entladen wird.  Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO\-Add\-Ins, wenn es geladen wird, und zum Bereinigen von Ressourcen, die vom VSTO\-Add\-In verwendet werden, wenn es entladen wird.  Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
#### So fügen Sie dem gespeicherten Dokument einen Textabsatz hinzu  
  
1.  Fügen Sie in der Codedatei "ThisAddIn" der Klasse `ThisAddIn` den folgenden Code hinzu.  Mit dem neuen Code wird ein Ereignishandler für das Ereignis <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> definiert, das ausgelöst wird, wenn ein Dokument gespeichert wird.  
  
     Wenn der Benutzer ein Dokument speichert, fügt der Ereignishandler am Anfang des Dokuments neuen Text hinzu.  
  
     [!code-csharp[Trin_WordAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/VB/ThisAddIn.vb#1)]  
  
    > [!NOTE]  
    >  Dieser Code verwendet den Indexwert 1, um auf den ersten Absatz in der Auflistung <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> zuzugreifen.  Obwohl Visual Basic und Visual C\# auf Null basierende Arrays verwenden, ist die untere Arraygrenze der meisten Auflistungen im Word\-Objektmodell 1.  Weitere Informationen finden Sie unter [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
2.  Wenn Sie C\# verwenden, fügen Sie dem `ThisAddIn_Startup`\-Ereignishandler den folgenden erforderlichen Code hinzu.  Dieser Code wird verwendet, um den `Application_DocumentBeforeSave`\-Ereignishandler mit dem Ereignis <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zu verbinden.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Zum  Ändern des Dokuments beim Speichern wurden in den vorherigen Codebeispielen die folgenden Objekte verwendet:  
  
-   Das Feld `Application` der Klasse `ThisAddIn`.  Das Feld `Application` gibt ein <xref:Microsoft.Office.Interop.Word.Application>\-Objekt zurück, das die aktuelle Instanz von Word darstellt.  
  
-   Der Parameter `Doc` des Ereignishandlers für das Ereignis <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  Der Parameter `Doc` ist ein <xref:Microsoft.Office.Interop.Word.Document>\-Objekt, das das gespeicherte Dokument darstellt.  Weitere Informationen finden Sie unter [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).  
  
## Testen des Projekts  
  
#### So testen Sie das Projekt  
  
1.  Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist.  Visual Studio erstellt außerdem einen Satz von Registrierungseinträgen, mit deren Hilfe Word das VSTO\-Add\-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO\-Add\-In ausgeführt werden kann.  Weitere Informationen finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Speichern Sie das aktive Dokument in Word.  
  
3.  Stellen Sie sicher, dass dem Dokument der folgende Text hinzugefügt wurde.  
  
     **Dieser Text wurde mithilfe von Code hinzugefügt.**  
  
4.  Schließen Sie Word.  
  
## Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO\-Add\-In\-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer.  Andernfalls wird das VSTO\-Add\-In weiterhin jedes Mal ausgeführt, wenn Sie Word auf dem Entwicklungscomputer öffnen.  
  
#### So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## Nächste Schritte  
 Nachdem Sie nun ein einfaches VSTO\-Add\-In für Word erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO\-Add\-Ins erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in VSTO\-Add\-Ins ausführen können: [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Programmieren von Aufgaben, die für Word\-VSTO\-Add\-Ins spezifisch sind: [Word-Projektmappen](../vsto/word-solutions.md).  
  
-   Verwenden des Objektmodells von Word: [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).  
  
-   Anpassen der Benutzeroberfläche \(User Interface, UI\) von Word, beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines benutzerdefinierten Aufgabenbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Erstellen und Debuggen von VSTO\-Add\-Ins für Word: [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von VSTO\-Add\-Ins für Word: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  