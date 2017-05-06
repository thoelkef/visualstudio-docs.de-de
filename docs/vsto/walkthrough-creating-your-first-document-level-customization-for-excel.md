---
title: "Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene f&#252;r Excel"
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
  - "Excel [Office-Entwicklung in Visual Studio], Erstellen eines ersten Projekts"
  - "Office-Entwicklung in Visual Studio, Erstellen eines ersten Projekts"
ms.assetid: 785d3b86-5ed5-4e0d-b5ee-896b6b1330ac
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene f&#252;r Excel
  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Excel.  Die Features, die Sie in dieser Art von Projektmappe erstellen, sind nur verfügbar, wenn eine bestimmte Arbeitsmappe geöffnet ist.  Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen vorzunehmen, z. B., um eine neue Registerkarte des Menübands anzuzeigen, wenn eine Arbeitsmappe geöffnet ist.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Excel\-Arbeitsmappenprojekts.  
  
-   Hinzufügen von Text zu einem Arbeitsblatt, das im Visual Studio\-Designer gehostet wird.  
  
-   Schreiben von Code, der das Excel\-Objektmodell zum Hinzufügen von Text zum angepassten Arbeitsblatt verwendet, wenn dieses geöffnet wird.  
  
-   Erstellen und Ausführen des Projekts, um es zu testen.  
  
-   Bereinigen des abgeschlossenen Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Erstellen des Projekts  
  
#### So erstellen Sie ein neues Excel\-Arbeitsmappenprojekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder **Visual Basic** und dann **Office\/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office\/SharePoint** den Knoten **Office\-Add\-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein Excel\-VSTO\-Add\-In\-Projekt aus.  
  
6.  Geben Sie im Feld **Name** die Angabe **FirstWorkbookCustomization** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     Der **Projekt\-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
8.  Wählen Sie **Neues Dokument erstellen** aus, und klicken Sie auf **OK**.  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt **FirstWorkbookCustomization** und fügt dem Projekt die folgenden Dateien hinzu.  
  
    -   "*FirstWorkbookCustomization*.xlsx" – stellt die Excel\-Arbeitsmappe im Projekt dar.  Enthält alle Arbeitsblätter und Diagramme.  
  
    -   "Sheet1" \(VB\-Datei für Visual Basic oder CS\-Datei für Visual C\#\) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das erste Arbeitsblatt in der Arbeitsmappe bereitstellt.  Weitere Informationen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  
  
    -   "Sheet2" \(VB\-Datei für Visual Basic oder CS\-Datei für Visual C\#\) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das zweite Arbeitsblatt in der Arbeitsmappe bereitstellt.  
  
    -   "Sheet3" \(VB\-Datei für Visual Basic oder CS\-Datei für Visual C\#\) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das dritte Arbeitsblatt in der Arbeitsmappe bereitstellt.  
  
    -   "ThisWorkbook" \(VB\-Datei für Visual Basic oder CS\-Datei für Visual C\#\) – enthält die Entwurfsoberfläche und den Code für Anpassungen auf Arbeitsmappenebene.  Weitere Informationen finden Sie unter [Arbeitsmappenhostelement](../vsto/workbook-host-item.md).  
  
     Die Codedatei "Sheet1" wird automatisch im Designer geöffnet.  
  
## Schließen und erneutes Öffnen von Arbeitsblättern im Designer  
 Wenn Sie eine Arbeitsmappe oder ein Arbeitsblatt absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie sie bzw. es erneut öffnen.  
  
#### So schließen Sie ein Arbeitsblatt im Designer und öffnen es erneut  
  
1.  Schließen Sie die Arbeitsmappe, indem Sie auf die Schaltfläche **Schließen** \(X\) für das Designerfenster klicken.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Codedatei **Sheet1**, und klicken Sie dann auf **Ansicht\-Designer**.  
  
     \- oder \-  
  
     Doppelklicken Sie im **Projektmappen\-Explorer** auf die Codedatei **Sheet1**.  
  
## Hinzufügen von Text zu einem Arbeitsblatt im Designer  
 Sie können die Benutzeroberfläche \(User Interface, UI\) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Arbeitsblatt ändern.  Beispielsweise können Sie Zellen Text hinzufügen, Formeln anwenden oder Excel\-Steuerelemente hinzufügen.  Weitere Informationen zur Verwendung des Designers finden Sie unter[Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### So fügen Sie einem Arbeitsblatt mithilfe des Designers Text hinzu  
  
1.  Wählen Sie in dem Arbeitsblatt, das im Designer geöffnet ist, die Zelle**A1** aus, und geben Sie dann den folgenden Text ein.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
> [!WARNING]  
>  Wenn Sie diese Textzeile der Zelle **A2** hinzufügen, wird sie von anderem Code in diesem Beispiel überschrieben.  
  
## Programmgesteuertes Hinzufügen von Text zu einem Arbeitsblatt  
 Als Nächstes fügen Sie der Codedatei "Sheet1" Code hinzu.  Der neue Code verwendet das Excel\-Objektmodell, um der Arbeitsmappe eine zweite Textzeile hinzuzufügen.  Standardmäßig enthält die Codedatei "Sheet1" den folgenden generierten Code:  
  
-   Eine partielle Definition der `Sheet1`\-Klasse, die das Programmiermodell des Arbeitsblatts darstellt und den Zugriff auf das Excel\-Objektmodell bereitstellt.  Weitere Informationen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).  Der Rest der `Sheet1`\-Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `Sheet1_Startup` und `Sheet1_Shutdown`.  Diese Ereignishandler werden aufgerufen, wenn Ihre Anpassung von Excel geladen und entladen wird.  Verwenden Sie diese Ereignishandler zum Initialisieren der Anpassung, wenn sie geladen wird, und zum Bereinigen der von der Anpassung verwendeten Ressourcen, wenn sie entladen wird.  Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
#### So fügen Sie dem Arbeitsblatt mithilfe von Code eine zweite Textzeile hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1**, und klicken Sie dann auf **Code anzeigen**.  
  
     Die Codedatei wird in Visual Studio geöffnet.  
  
2.  Ersetzen Sie den `Sheet1_Startup`\-Ereignishandler durch den folgenden Code.  Beim Öffnen von "Sheet1" wird dem Arbeitsblatt durch diesen Code eine zweite Textzeile hinzugefügt.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/CS/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/VB/Sheet1.vb#1)]  
  
## Testen des Projekts  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die der Arbeitsmappe zugeordnet ist.  Visual Studio legt eine Kopie der Arbeitsmappe und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann.  Weitere Informationen finden Sie unter [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Vergewissern Sie sich, dass der folgende Text in der Arbeitsmappe angezeigt wird.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
3.  Schließen Sie die Arbeitsmappe.  
  
## Bereinigen des Projekts  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.  
  
#### So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer  
  
1.  Klicken Sie in Visual Studio im Menü **Erstellen** auf **Projektmappe bereinigen**.  
  
## Nächste Schritte  
 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Excel erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokumentebene ausführen können: [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
-   Programmieraufgaben, die für Anpassungen auf Dokumentebene für Excel spezifisch sind: [Excel-Projektmappen](../vsto/excel-solutions.md).  
  
-   Verwenden des Objektmodells von Excel: [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
-   Anpassen der Benutzeroberfläche \(User Interface, UI\) von Excel, beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Verwenden erweiterter Excel\-Objekte, die von Office\-Entwicklungstools in Visual Studio zum Ausführen von Aufgaben bereitgestellt werden, die mithilfe des Excel\-Objektmodells nicht möglich sind \(z. B. das Hosten verwalteter Steuerelemente für Dokumente und das Binden von Excel\-Steuerelementen an Daten mithilfe des Datenbindungsmodells von Windows Forms\): [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Erstellen und Debuggen von Anpassungen auf Dokumentebene für Excel: [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von Anpassungen auf Dokumentebene für Excel: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
  
  