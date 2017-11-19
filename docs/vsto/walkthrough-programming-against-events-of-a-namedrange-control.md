---
title: "Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements | Microsoft Docs"
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
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40076f607e66ec76aaa42ae297d22b38a6234ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements
  Diese exemplarische Vorgehensweise veranschaulicht das Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements zu einem Microsoft Office Excel-Arbeitsblatt und das Programmieren der Ereignisse, die mithilfe der Office-Entwicklungstools in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement einem Arbeitsblatt.  
  
-   Programmierung mit <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelementereignissen.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt mit Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **My Named Range Events**. Stellen Sie sicher, dass **erstellen Sie ein neues Dokument** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **My Named Range Events** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Hinzufügen von Text und benannte Bereiche in das Arbeitsblatt  
 Da Hoststeuerelemente erweiterte Office-Objekte sind, können Sie diese hinzufügen zu Ihrem Dokument auf die gleiche Weise fügen Sie das systemeigene Objekt. Sie können z. B. eine Excel hinzufügen <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement einem Arbeitsblatt durch Öffnen der **einfügen** zeigen Sie im Menü **Namen**, und wählen Sie **definieren**. Sie können auch Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement durch Ziehen von der **Toolbox** in das Arbeitsblatt.  
  
 In diesem Schritt fügen Sie zwei NamedRange-Steuerelementen zum Arbeitsblatt mithilfe der **Toolbox**, und fügen Sie Text in das Arbeitsblatt hinzu.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>So fügen Sie einen Bereich in das Arbeitsblatt hinzu  
  
1.  Überprüfen Sie, ob die **eigene benannte Bereich Events.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.  
  
2.  Aus der **Excel-Steuerelementen** Registerkarte Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1** in `Sheet1`.  
  
     Die **Hinzufügen von NamedRange-Steuerelement** Dialogfeld wird angezeigt.  
  
3.  Überprüfen Sie, ob **$A$ 1** wird angezeigt, in das Bearbeitungsfeld, und dass die Zelle **A1** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **A1** um es auszuwählen.  
  
4.  Klicken Sie auf **OK**.  
  
     Zelle **A1** wird zu einem Bereich mit dem Namen `namedRange1`. Es ist nicht erkennbar, auf dem Arbeitsblatt jedoch `namedRange1` wird angezeigt, der **Name** Feld (oberhalb des Arbeitsblatts auf der linken Seite) Wenn Zelle **A1** ausgewählt ist.  
  
5.  Fügen Sie einen anderen <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **B3**.  
  
6.  Überprüfen Sie, ob **$B$ 3** wird angezeigt, in das Bearbeitungsfeld, und dass die Zelle **B3** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **B3** um es auszuwählen.  
  
7.  Klicken Sie auf **OK**.  
  
     Zelle **B3** wird zu einem Bereich mit dem Namen `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>So fügen Sie Text in das Arbeitsblatt hinzu  
  
1.  In der Zelle **A1**, geben Sie den folgenden Text:  
  
     **Dies ist ein Beispiel für ein NamedRange-Steuerelement.**  
  
2.  In der Zelle **A3** (auf der linken Seite des `namedRange2`), geben Sie den folgenden Text:  
  
     **Ereignisse:**  
  
 In den folgenden Abschnitten, Schreiben Sie Code, der in Text eingefügt `namedRange2` und ändert die Eigenschaften der `namedRange2` Steuerelement als Antwort auf die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, und <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignisse `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Hinzufügen von Code für die Reaktion auf das BeforeDoubleClick-Ereignis  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Zum Einfügen von Text in NamedRange2 basierend auf dem BeforeDoubleClick-Ereignis  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs** , und wählen Sie **Code anzeigen**.  
  
2.  Fügen Code hinzu, sodass der `namedRange1_BeforeDoubleClick` Ereignishandler sieht wie folgt:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  In c# müssen Sie Ereignishandler für den benannten Bereich hinzufügen, entsprechend der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis unten. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>So reagieren Sie auf das Änderungsereignis Code hinzufügen  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Zum Einfügen von Text in namedRange2 basierend auf das Change-Ereignis  
  
1.  Fügen Code hinzu, sodass der `NamedRange1_Change` Ereignishandler sieht wie folgt:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Da durch Doppelklicken auf eine Zelle in einem Excel-Bereich der Bearbeitungsmodus aktiviert, wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Ereignis tritt auf, wenn die Auswahl außerhalb des Bereichs verschoben wird, selbst wenn keine Änderungen an Text aufgetreten ist.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Hinzufügen von Code für die Reaktion auf das SelectionChange-Ereignis  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Zum Einfügen von Text in namedRange2 basierend auf den SelectionChange-Ereignis  
  
1.  Fügen Code hinzu, sodass der **NamedRange1_SelectionChange** Ereignishandler sieht wie folgt:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Da bewirkt, die Auswahl dass für das Verschieben in den Bereich durch Doppelklicken auf eine Zelle in einem Excel-Bereich eine <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignis tritt auf, bevor Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> Ereignis tritt auf.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Nun können Sie die Arbeitsmappe, um zu überprüfen, ob dieses Texts, beschreibt die Ereignisse Testen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement wird in einen anderen benannten Bereich eingefügt, wenn die Ereignisse ausgelöst werden.  
  
#### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Platzieren Sie den Cursor in `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf die <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignis eingefügt wird, und, die ein Kommentar in das Arbeitsblatt eingefügt wird.  
  
3.  Doppelklicken klicken Sie in `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> Ereignisse wird mit rotem kursiv in eingefügt `namedRange2`.  
  
4.  Klicken Sie außerhalb des `namedRange1` und beachten Sie, dass das Change-Ereignis tritt bei beenden den Bearbeitungsmodus, obwohl keine Änderung auf den Text vorgenommen wurde.  
  
5.  Ändern des Texts innerhalb `namedRange1`.  
  
6.  Klicken Sie außerhalb des `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Ereignis wird mit blauem Text in eingefügt `namedRange2`.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen von Programmieren anhand von Ereignissen von einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement. Hier ist eine Aufgabe, die anschließen:  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  