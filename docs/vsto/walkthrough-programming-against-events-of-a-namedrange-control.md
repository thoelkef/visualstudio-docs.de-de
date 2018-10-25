---
title: 'Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f8b55cda9576a0203857b3fdaeccbb205b42168
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812517"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements
  In dieser exemplarischen Vorgehensweise veranschaulicht das Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement zu einem Microsoft Office Excel-Arbeitsblatt und das Programmieren der Ereignisse mithilfe von Office-Entwicklungstools in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements zu einem Arbeitsblatt.  
  
-   Programmieren Sie mit <xref:Microsoft.Office.Tools.Excel.NamedRange> Ereignisse zu steuern.  
  
-   Testen Sie das Projekt ein.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
 In diesem Schritt erstellen Sie ein Excel-Workbook-Projekt mithilfe von Visual Studio.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **My mit dem Namen der Range-Events**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **My mit dem Namen der Range-Events** Projekt **Projektmappen-Explorer**.  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Fügen Sie Text und benannte Bereiche, in das Arbeitsblatt  
 Da die Host-Steuerelementen über erweiterte Office-Objekte sind, können Sie diese hinzufügen, das Dokument auf die gleiche Weise würden Sie das systemeigene Objekt hinzufügen. Sie können z. B. eine Excel hinzufügen <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements zu einem Arbeitsblatt durch Öffnen der **einfügen** zeigen Sie im Menü **Namen**, auswählen und **definieren**. Sie können auch Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelements durch Ziehen aus der **Toolbox** in das Arbeitsblatt.  
  
 In diesem Schritt fügen Sie zwei NamedRange-Steuerelementen mit dem Arbeitsblatt mithilfe der **Toolbox**, und klicken Sie dann Text in das Arbeitsblatt.  
  
### <a name="to-add-a-range-to-your-worksheet"></a>Hinzufügen eines Bereichs in das Arbeitsblatt  
  
1.  Überprüfen Sie, ob die *Meine benannte Bereich Events.xlsx* Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.  
  
2.  Von der **Excel-Steuerelemente** Registerkarte der Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1** in `Sheet1`.  
  
     Die **NamedRange-Steuerelement hinzufügen** Dialogfeld wird angezeigt.  
  
3.  Überprüfen Sie, ob **$A$ 1** wird in der editierbares Textfeld, und dieser Zelle **A1** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **A1** um es auszuwählen.  
  
4.  Klicken Sie auf **OK**.  
  
     Zelle **A1** wird zu einem Bereich mit dem Namen `namedRange1`. Gibt es dafür keinen sichtbaren Hinweis auf dem Arbeitsblatt aber `namedRange1` wird in der **Namen** Feld (befindet sich direkt über dem Arbeitsblatt auf der linken Seite) Wenn Zelle **A1** ausgewählt ist.  
  
5.  Fügen Sie ein weiteres <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **B3**.  
  
6.  Überprüfen Sie, ob **$B$ 3** wird in der editierbares Textfeld, und dieser Zelle **B3** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **B3** um es auszuwählen.  
  
7.  Klicken Sie auf **OK**.  
  
     Zelle **B3** wird zu einem Bereich mit dem Namen `namedRange2`.  
  
### <a name="to-add-text-to-your-worksheet"></a>Hinzufügen von Text in das Arbeitsblatt  
  
1. In der Zelle **A1**, geben Sie den folgenden Text:  
  
    **Dies ist ein Beispiel für ein NamedRange-Steuerelement.**  
  
2. In der Zelle **A3** (auf der linken Seite des `namedRange2`), geben Sie den folgenden Text:  
  
    **Ereignisse:**  
  
   In den folgenden Abschnitten, Schreiben Sie Code, mit dem Text in eingefügt `namedRange2` und ändert die Eigenschaften der `namedRange2` Steuerelement als Reaktion auf die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, und <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignisse `namedRange1`.  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Fügen Sie Code zum Reagieren auf das Ereignis BeforeDoubleClick hinzu  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Zum Einfügen von Text in NamedRange2 basierend auf dem BeforeDoubleClick-Ereignis  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs** , und wählen Sie **Ansichtscode**.  
  
2.  Fügen Code hinzu, sodass die `namedRange1_BeforeDoubleClick` Ereignishandler sieht wie folgt aus:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  In c# müssen Sie Ereignishandler für den benannten Bereich hinzufügen, siehe die <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis unten. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>Fügen Sie Code zum Reagieren auf das Change-Ereignis  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Zum Einfügen von Text in namedRange2 basierend auf das Change-Ereignis  
  
1.  Fügen Code hinzu, sodass die `NamedRange1_Change` Ereignishandler sieht wie folgt aus:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Da durch Doppelklicken auf eine Zelle in einem Excel-Bereich den Bearbeitungsmodus versetzt, wird eine <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Ereignis tritt auf, wenn die Auswahl außerhalb des Bereichs verschoben wird, selbst wenn keine Änderungen an Text aufgetreten ist.  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Fügen Sie Code zum Antworten auf die SelectionChange-Ereignis  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Zum Einfügen von Text in namedRange2 basierend auf den SelectionChange-Ereignis  
  
1.  Fügen Code hinzu, sodass die **NamedRange1_SelectionChange** Ereignishandler sieht wie folgt aus:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Da bewirkt, die Auswahl zum Verschieben in den Bereich durch Doppelklicken auf eine Zelle in einem Excel-Bereich dass eine <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignis tritt auf, bevor Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> Ereignis auftritt.  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Nun können Sie die Arbeitsmappe, um zu überprüfen, ob dieser Text beschreibt die Ereignisse des Testen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement wird in einen anderen benannten Bereich eingefügt, wenn die Ereignisse ausgelöst werden.  
  
### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie **F5** um Ihr Projekt auszuführen.  
  
2.  Platzieren Sie den Cursor in `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf die <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> Ereignis eingefügt wird, und, die ein Kommentar in das Arbeitsblatt eingefügt wird.  
  
3.  Klicken Sie auf doppelte `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> kursiven Text in Rot eingefügt wird `namedRange2`.  
  
4.  Klicken Sie außerhalb des `namedRange1` und beachten Sie, dass das Change-Ereignis tritt auf, beim Beenden den Bearbeitungsmodus, obwohl keine Änderungen am Text vorgenommen wurde.  
  
5.  Ändern Sie den Text in `namedRange1`.  
  
6.  Klicken Sie außerhalb des `namedRange1`, und überprüfen Sie, ob der Text im Hinblick auf <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> Ereignis wird mit blauem Text in eingefügt `namedRange2`.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen der Programmierung mit Ereignissen eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement. Hier ist eine Aufgabe, die als Nächstes getan werden kann:  
  
-   Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  