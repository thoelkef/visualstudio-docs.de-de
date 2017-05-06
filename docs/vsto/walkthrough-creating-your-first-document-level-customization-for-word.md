---
title: "Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene f&#252;r Word"
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
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
  - "Office-Entwicklung in Visual Studio, Erstellen eines ersten Projekts"
  - "Word [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene f&#252;r Word
  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Word.  Die Features, die Sie in dieser Art von Lösung erstellen, sind nur verfügbar, wenn ein bestimmtes Dokument geöffnet ist.  Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen \(z. B. eine neue Registerkarte des Menübands anzuzeigen, wenn ein Dokument geöffnet ist\) vorzunehmen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Word\-Dokumentprojekts.  
  
-   Hinzufügen von Text zu dem Dokument, das in Visual Studio\-Designer gehostet wird.  
  
-   Schreiben von Code, der das Word\-Objektmodell zum Hinzufügen von Text zum angepassten Dokument verwendet, wenn dieses geöffnet wird.  
  
-   Erstellen und Ausführen des Projekts, um es zu testen.  
  
-   Bereinigen des Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Erstellen des Projekts  
  
#### So erstellen Sie ein neues Word\-Dokumentprojekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder  **Visual Basic** und dann **Office\/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office\/SharePoint** den Knoten **Office\-Add\-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein Word VSTO\-Dokumentprojekt aus.  
  
6.  Geben Sie im Feld **Name** die Angabe **FirstDocumentCustomization** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     Der **Projekt\-Assistent aus Visual Studio Tools für Office** wird geöffnet.  
  
8.  Wählen Sie **Neues Dokument erstellen** aus, und klicken Sie dann auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt **FirstDocumentCustomization** und fügt das Dokument **FirstDocumentCustomization** und die Codedatei "ThisDocument" dem Projekt hinzu.  Das Dokument **FirstDocumentCustomization** wird automatisch im Designer geöffnet.  
  
## Schließen und erneutes Öffnen des Dokuments im Designer  
 Wenn Sie das Dokument absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie es erneut öffnen.  
  
#### So schließen Sie das Dokument im Designer und öffnen es erneut  
  
1.  Schließen Sie das Dokument, indem Sie auf die Schaltfläche **Schließen** \(X\) für das Designer\-Fenster klicken.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Codedatei **ThisDocument**, und klicken Sie dann auf **Ansicht\-Designer**.  
  
     \- oder \-  
  
     Doppelklicken Sie im **Projektmappen\-Explorer** auf die Codedatei **ThisDocument**.  
  
## Hinzufügen von Text zum Dokument im Designer  
 Sie können die Benutzeroberfläche \(User Interface, UI\) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Dokument ändern.  Sie können z. B. Text, Tabellen oder Word\-Steuerelemente hinzufügen.  Weitere Informationen zur Verwendung des Designers finden Sie unter[Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### So fügen Sie Ihrem Dokument mithilfe des Designers Text hinzu  
  
1.  Geben Sie den folgenden Text in das Dokument ein, das im Designer geöffnet ist.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
## Programmgesteuertes Hinzufügen von Text zum Dokument  
 Fügen Sie der Codedatei "ThisDocument " nun Code hinzu.  Der neue Code verwendet das Word\-Objektmodell, um dem Dokument einen zweiten Textabsatz hinzuzufügen.  Standardmäßig enthält die Codedatei "ThisDocument " den folgenden generierten Code:  
  
-   Eine partielle Definition der Klasse `ThisDocument`, die das Programmiermodell des Dokuments darstellt und den Zugriff auf das Word\-Objektmodell bereitstellt.  Weitere Informationen finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).  Die restliche Klasse `ThisDocument` wird in einer ausgeblendeten Codedatei definiert, die Sie nicht ändern sollten.  
  
-   Die `ThisDocument_Startup`\- und `ThisDocument_Shutdown`\-Ereignishandler.  Diese Ereignishandler werden aufgerufen, wenn das Dokument geöffnet und geschlossen wird.  Verwenden Sie diese Ereignishandler, um Ihre Anpassung zu initialisieren, wenn das Dokument geöffnet wird, sowie zum Bereinigen von Ressourcen, die von Ihrer Anpassung verwendet werden, wenn das Dokument geschlossen wird.  Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
#### So fügen Sie dem Dokument mithilfe von Code einen zweiten Textabsatz hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisDocument**, und klicken Sie dann auf **Code anzeigen**.  
  
     Die Codedatei wird in Visual Studio geöffnet.  
  
2.  Ersetzen Sie den `ThisDocument_Startup`\-Ereignishandler durch den folgenden Code.  Beim Öffnen des Dokuments fügt dieser Code dem Dokument einen zweiten Textabsatz hinzu.  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Dieser Code verwendet den Indexwert 1 in der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>, um auf den ersten Absatz zuzugreifen.  Obwohl Visual Basic und Visual C\# auf Null basierende Arrays verwenden, ist die untere Arraygrenze der meisten Auflistungen im Word\-Objektmodell 1.  Weitere Informationen finden Sie unter [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
## Testen des Projekts  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie **F5**, um Ihr Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die dem Dokument zugeordnet ist.  Visual Studio legt eine Kopie des Dokuments und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann.  Weitere Informationen finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Vergewissern Sie sich im Dokument, dass der folgende Text angezeigt wird.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
     **Dieser Text wurde mithilfe von Code hinzugefügt.**  
  
3.  Schließen Sie das Dokument.  
  
## Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.  
  
#### So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## Nächste Schritte  
 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Word erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokumentebene ausführen können: [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
-   Programmieraufgaben, die für Anpassungen auf Dokumentebene für Word spezifisch sind: [Word-Projektmappen](../vsto/word-solutions.md).  
  
-   Verwenden des Objektmodells von Word: [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).  
  
-   Anpassen der Benutzeroberfläche \(User Interface, UI\) von Word, beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Verwenden erweiterter Word\-Objekte, die von Office\-Projektmappen in Visual Studio zum Ausführen von Aufgaben bereitgestellt werden, die mithilfe des Word\-Objektmodells nicht möglich sind \(z. B. das Hosten verwalteter Steuerelemente für Dokumente und das Binden von Word\-Steuerelementen an Daten mithilfe des Datenbindungsmodells von Windows Forms\): [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Erstellen und Debuggen von Anpassungen auf Dokumentebene für Word: [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von Anpassungen auf Dokumentebene für Word: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  