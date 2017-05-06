---
title: "Exemplarische Vorgehensweise: Programmieren in Abh&#228;ngigkeit von Ereignissen eines NamedRange-Steuerelements"
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
  - "NamedRange-Steuerelement, Ereignisse"
  - "Bereiche, Behandeln von Ereignissen"
  - "Arbeitsblätter, Automatisieren"
  - "Arbeitsblätter, Ändern von Zellwerten"
  - "Arbeitsblätter, Ereignisse"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# Exemplarische Vorgehensweise: Programmieren in Abh&#228;ngigkeit von Ereignissen eines NamedRange-Steuerelements
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Excel\-Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzugefügt wird, und die Programmierung mit den Ereignissen mithilfe der Office\-Entwicklungstools in Visual Studio beschrieben.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements zu einem Arbeitsblatt.  
  
-   Programmieren in Abhängigkeit von Ereignissen des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Erstellen des Projekts  
 In diesem Schritt erstellen Sie mit Visual Studio ein Excel\-Arbeitsmappenprojekt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen My Named Range Events.  Stellen Sie sicher, dass **Neues Dokument erstellen** ausgewählt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet eine neue Excel\-Arbeitsmappe im Designer und fügt im **Projektmappen\-Explorer** das Projekt "My Named Range Events" hinzu.  
  
## Hinzufügen von Text und benannten Bereichen zum Arbeitsblatt  
 Da Hoststeuerelemente erweiterte Office\-Objekte sind, können Sie sie einem Dokument auf dieselbe Weise wie systemeigene Objekte hinzufügen.  Sie können dem Arbeitsblatt z. B. ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement in Excel hinzufügen, indem Sie das Menü **Einfügen** öffnen, auf **Name** zeigen und **Definieren** auswählen.  Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auch hinzufügen, indem Sie es aus der **Toolbox** auf das Arbeitsblatt ziehen.  
  
 In diesem Schritt fügen Sie dem Arbeitsblatt mithilfe der **Toolbox** zwei benannte Bereichssteuerelemente hinzu und fügen dann Text in das Arbeitsblatt ein.  
  
#### So fügen Sie dem Arbeitsblatt einen Bereich hinzu  
  
1.  Überprüfen Sie, ob die **My Named Range Events.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit `Sheet1` angezeigt.  
  
2.  Ziehen Sie von der Registerkarte **Excel\-Steuerelemente** der Toolbox ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auf Zelle **A1** von `Sheet1`.  
  
     Das Dialogfeld **NamedRange\-Steuerelement hinzufügen** wird angezeigt.  
  
3.  Vergewissern Sie sich, dass **$A$1** im bearbeitbaren Textfeld angezeigt wird und dass Zelle **A1** ausgewählt ist.  Wenn dies nicht der Fall ist, klicken Sie auf Zelle **A1**, um sie auszuwählen.  
  
4.  Klicken Sie auf **OK**.  
  
     Die Zelle **A1** wird zu einem Bereich mit dem Namen `namedRange1`.  Auf dem Arbeitsblatt befindet sich kein sichtbarer Hinweis darauf, jedoch wird bei Auswahl der Zelle **A1** im Feld **Name** \(gleich links über dem Arbeitsblatt\) `namedRange1` angezeigt.  
  
5.  Fügen Sie Zelle **B3** ein weiteres <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzu.  
  
6.  Vergewissern Sie sich, dass **$B$3** im bearbeitbaren Textfeld angezeigt wird und dass Zelle **B3** ausgewählt ist.  Wenn dies nicht der Fall ist, klicken Sie auf Zelle **B3**, um sie auszuwählen.  
  
7.  Klicken Sie auf **OK**.  
  
     Die Zelle **B3** wird zu einem Bereich mit dem Namen `namedRange2`.  
  
#### So fügen Sie dem Arbeitsblatt Text hinzu  
  
1.  Geben Sie in Zelle **A1** den folgenden Text ein:  
  
     This is an example of a NamedRange control.  
  
2.  Geben Sie in der Zelle **A3** \(links von `namedRange2`\) den folgenden Text ein:  
  
     Events:  
  
 In den folgenden Abschnitten wird Code dargestellt, der in `namedRange2` Text einfügt und als Antwort auf das <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>\-Ereignis, das <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>\-Ereignis und das <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>\-Ereignis von `namedRange1` die Eigenschaften des `namedRange2`\-Steuerelements ändert.  
  
## Hinzufügen von Code, der auf das BeforeDoubleClick\-Ereignis reagiert  
  
#### So fügen Sie auf der Grundlage des BeforeDoubleClick\-Ereignisses Text in NamedRange2 ein  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1.vb** bzw. **Sheet1.cs**, und wählen Sie **Code anzeigen** aus.  
  
2.  Fügen Sie Code hinzu, sodass der `namedRange1_BeforeDoubleClick`\-Ereignishandler wie folgt aussieht:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  In C\# müssen Sie für den benannten Bereich Ereignishandler hinzufügen, wie weiter unten im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignis gezeigt wird.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Hinzufügen von Code, der auf das Change\-Ereignis reagiert  
  
#### So fügen Sie auf der Grundlage des Change\-Ereignisses Text in namedRange2 ein  
  
1.  Fügen Sie Code hinzu, sodass der `NamedRange1_Change`\-Ereignishandler folgendermaßen aussieht:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Da durch Doppelklicken auf eine Zelle in einem Excel\-Bereich der Bearbeitungsmodus gestartet wird, wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>\-Ereignis ausgelöst, wenn eine Auswahl aus dem Bereich heraus verschoben wird, auch wenn keine Änderungen am Text vorgenommen werden.  
  
## Hinzufügen von Code, der auf das SelectionChange\-Ereignis reagiert  
  
#### So fügen Sie auf der Grundlage des SelectionChange\-Ereignisses Text in namedRange2 ein  
  
1.  Fügen Sie Code hinzu, sodass der **NamedRange1\_SelectionChange**\-Ereignishandler folgendermaßen aussieht:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Da durch Doppelklicken auf eine Zelle in einem Excel\-Bereich die Auswahl in den Bereich verschoben wird, wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>\-Ereignis ausgelöst, bevor das <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>\-Ereignis auftritt.  
  
## Testen der Anwendung  
 Nun können Sie die Arbeitsmappe testen, um zu überprüfen, ob Text, der die Ereignisse eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements beschreibt, beim Auslösen der Ereignisse in einen anderen benannten Bereich eingefügt wird.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Platzieren Sie den Cursor in `namedRange1`, und vergewissern Sie sich, dass der das <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>\-Ereignis betreffende Text und ein Kommentar in das Arbeitsblatt eingefügt werden.  
  
3.  Doppelklicken Sie in `namedRange1`, und vergewissern Sie sich, dass der die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>\-Ereignisse betreffende Text rot und kursiv formatiert in `namedRange2` eingefügt wird.  
  
4.  Klicken Sie außerhalb von `namedRange1`, und beachten Sie, dass das Change\-Ereignis auch dann auftritt, wenn der Bearbeitungsmodus beendet und keine Änderungen am Text vorgenommen wurden.  
  
5.  Ändern Sie den Text in `namedRange1`.  
  
6.  Klicken Sie außerhalb von `namedRange1`, und vergewissern Sie sich, dass der das <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>\-Ereignis betreffende Text blau formatiert in `namedRange2` eingefügt wird.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen des Programmierens in Abhängigkeit von Ereignissen eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements erläutert.  Hier ist eine Aufgabe, die danach kommen könnte:  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Siehe auch  
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  