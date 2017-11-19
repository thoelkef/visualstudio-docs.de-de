---
title: "Aktionsbereichsübersicht | Microsoft Docs"
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
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: "101"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c9d8bd58c8dabc1114b3516e518992b0f91bc173
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="actions-pane-overview"></a>Aktionsbereichsübersicht
  Ein Aktionsbereich ist ein anpassbarer **Dokumentaktionen** Aufgabenbereich, der an ein bestimmtes Microsoft Office Word-Dokument oder Microsoft Office Excel-Arbeitsmappe angefügt ist. Es gehostet wird in den Office-Aufgabenbereich zusammen mit weiteren integrierten Aufgabenbereichen wie dem **XML-Quelle** Aufgabenbereich in Excel oder den **Formatvorlagen und Formatierung** Aufgabenbereich in Word. Sie können Windows Forms-Steuerelemente oder WPF-Steuerelemente verwenden, um die Benutzeroberfläche des Aktionsbereichs zu gestalten.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können einen Aktionsbereich nur in einer Anpassung auf Dokumentebene für Word oder Excel erstellen. In einem VSTO-Add-In können Sie keinen Aktionsbereich erstellen. Weitere Informationen finden Sie unter [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Der Aktionsbereich unterscheidet sich von benutzerdefinierten Aufgabenbereichen. Benutzerdefinierte Aufgabenbereiche sind der Anwendung und keinem bestimmten Dokument zugeordnet. Sie können benutzerdefinierte Aufgabenbereiche in VSTO-Add-Ins für einige Microsoft Office-Anwendungen erstellen. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie führen I: verwenden WPF-Steuerelemente in einem Excel-Aktionsbereich?](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## <a name="displaying-the-actions-pane"></a>Anzeigen des Aktionsbereichs  
 Der Aktionsbereich wird durch die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse dargestellt. Wenn Sie ein Projekt auf Dokumentebene erstellen, machen Sie eine Instanz dieser Klasse für Ihren Code verfügbar, indem Sie das `ActionsPane`-Feld der `ThisWorkbook`-Klasse (für Excel) oder der `ThisDocument`-Klasse (für Word) im Projekt verwenden. Um den Aktionsbereich anzuzeigen, fügen Sie der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>-Eigenschaft des `ActionsPane`-Felds ein Windows Forms-Steuerelement hinzu. Durch das folgende Codebeispiel wird dem Aktionsbereich ein Steuerelement namens `actions` hinzugefügt.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
 Der Aktionsbereich wird zur Laufzeit sichtbar, sobald Sie ihm explizit ein Steuerelement hinzufügen. Sobald der Aktionsbereich angezeigt wird, können Sie dynamisch Steuerelemente in Reaktion auf Benutzeraktionen dynamisch hinzufügen oder entfernen. Normalerweise fügen Sie den Code hinzu, um den Aktionsbereich im `Startup`-Ereignishandler von `ThisDocument` oder `ThisWorkbook` anzuzeigen, damit der Aktionsbereich sichtbar ist, wenn der Benutzer das Dokument erstmalig öffnet. Sie können den Aktionsbereich jedoch auch ausschließlich als Reaktion auf eine Benutzeraktion im Dokument anzeigen. Sie können den Code beispielsweise zum `Click`-Ereignis eines Steuerelements im Dokument hinzufügen.  
  
### <a name="adding-multiple-controls-to-the-actions-pane"></a>Hinzufügen mehrerer Steuerelemente im Aktionsbereich  
 Wenn Sie mehrere Steuerelemente zum Aktionsbereich hinzufügen, sollten Sie die Steuerelemente in den meisten Fällen in einem Benutzersteuerelement gruppieren und das Benutzersteuerelement dann der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>-Eigenschaft hinzufügen. Dieser Vorgang umfasst die folgenden Schritte:  
  
1.  Erstellen Sie die Benutzeroberfläche (UI) des Aktionsbereichs, indem ein **Aktionsbereich-Steuerelement** oder **Benutzersteuerelement** Element aus, um das Projekt. Beide Elemente umfassen eine benutzerdefinierte Windows Forms-<xref:System.Windows.Forms.UserControl>-Klasse. Die **Aktionsbereich-Steuerelement** und **Benutzersteuerelement** sind gleich; der einzige Unterschied ist, deren Namen.  
  
2.  Fügen Sie dem <xref:System.Windows.Forms.UserControl> Windows Forms-Steuerelemente durch Verwendung des Designers oder durch Schreiben von Code hinzu.  
  
    > [!NOTE]  
    >  Sie können dem Aktionsbereich auch WPF-Steuerelemente hinzufügen, indem Sie dem Windows Forms-<xref:System.Windows.Forms.UserControl> ein WPF-<xref:System.Windows.Controls.UserControl> hinzufügen. Weitere Informationen finden Sie unter [Verwenden von WPF-Steuerelementen in Office-Projektmappen](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Fügen Sie den im `ActionsPane`-Feld enthaltenen Steuerelementen der `ThisWorkbook`-Klasse (für Excel) oder der `ThisDocument`-Klasse (für Word) eine Instanz des benutzerdefinierten Steuerelements im Projekt hinzu.  
  
 Beispiele, in denen dieser Prozess ausführlicher veranschaulicht, finden Sie unter [wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## <a name="hiding-the-actions-pane"></a>Ausblenden des Aktionsbereichs  
 Obwohl die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse über eine <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A>-Methode und eine <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>-Eigenschaft verfügt, können Sie den Aktionsbereich nicht von der Benutzeroberfläche entfernen, indem Sie einen beliebigen Member der <xref:Microsoft.Office.Tools.ActionsPane>-Klasse selbst verwenden. Aufrufen der <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> -Methode oder Festlegen der <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Eigenschaft **"false"** blendet nur die Steuerelemente im Aktionsbereich ausgeblendet und nicht im Aufgabenbereich.  
  
 Um den Aufgabenbereich in der Projektmappe auszublenden, haben Sie mehrere Optionen:  
  
-   Legen Sie für Word die <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> Eigenschaft von der <xref:Microsoft.Office.Interop.Word.TaskPane> Objekt, das im Aufgabenbereich "Dokumentaktionen", um darstellt **"false"**. Das folgende Codebeispiel sollte von der `ThisDocument`-Klasse im Projekt ausgeführt werden.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  
  
-   Legen Sie für Excel die <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> Eigenschaft von der <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> -Objekt **"false"**. Das folgende Codebeispiel sollte von der `ThisWorkbook`-Klasse im Projekt ausgeführt werden.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  
  
-   Sie können alternativ festlegen, für Word oder Excel, die <xref:Microsoft.Office.Core.CommandBar.Visible%2A> -Eigenschaft der Befehlsleiste, die den Aufgabenbereich darstellt **"false"**. Das folgende Codebeispiel sollte von der `ThisDocument`-Klasse oder `ThisWorkbook`-Klasse im Projekt ausgeführt werden.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  
  
### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Löschen des Aktionsbereichs beim Öffnen des Dokuments  
 Wenn der Benutzer das Dokument speichert, während der Aktionsbereich angezeigt wird, ist der Aktionsbereich bei jedem Öffnen des Dokuments sichtbar, und zwar unabhängig davon, ob der Aktionsbereich Steuerelemente enthält oder nicht. Wenn Sie die Anzeige steuern möchten, rufen Sie die <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A>-Methode des `ActionsPane`-Felds im `Startup`-Ereignishandler von `ThisDocument` oder `ThisWorkbook` ab, um sicherzustellen, dass der Aktionsbereich beim Öffnen des Dokuments nicht sichtbar ist.  
  
### <a name="determining-when-the-actions-pane-is-closed"></a>Festlegen, wann der Aktionsbereich geschlossen wird  
 Es gibt kein Ereignis, das beim Schließen des Aktionsbereichs ausgelöst wird. Obwohl die <xref:Microsoft.Office.Tools.ActionsPane>-Klasse über ein <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>-Ereignis verfügt, wird dieses Ereignis nicht ausgelöst, wenn der Endbenutzer den Aktionsbereich schließt. Stattdessen dieses Ereignis wird ausgelöst, wenn die Steuerelemente im Aktionsbereich, durch Aufrufen ausgeblendet sind der <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> Methode oder durch Festlegen der <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Eigenschaft **"false"**.  
  
 Wenn der Endbenutzer den Aktionsbereich schließt, kann der Benutzer ihn erneut anzeigen, indem er eines der folgenden Verfahren in der Benutzeroberfläche (UI) der Anwendung ausführt.  
  
##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>So zeigen Sie den Aktionsbereich mithilfe der Benutzeroberfläche von Word oder Excel an  
  
1.  Klicken Sie auf dem Menüband auf die **Ansicht** Registerkarte.  
  
2.  In der **ein-/ausblenden** zu gruppieren, klicken Sie auf die **Dokumentaktionen** Umschaltfläche.  
  
## <a name="programming-actions-pane-events"></a>Programmieren der Ereignisse für den Aktionsbereich  
 Sie können dem Aktionsbereich mehrere Benutzersteuerelemente hinzufügen und dann Code schreiben, der durch Ein- oder Ausblenden der Benutzersteuerelemente auf Ereignisse im Dokument reagiert. Wenn Sie Ihrem Dokument XML-Schemaelemente zuordnen, können Sie bestimmte Benutzersteuerelemente im Aktionsbereich einblenden, sobald sich der Einfügepunkt innerhalb eines der XML-Elemente befindet. Weitere Informationen finden Sie unter [wie: Zuordnen von Schemas zu Word-Dokumente in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) und [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 Sie können auch Code schreiben, der auf Ereignisse eines beliebigen Objekts, z. B. Hoststeuerelement-, Anwendungs- oder Dokumentereignisse, reagiert. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## <a name="binding-data-to-controls-on-the-actions-pane"></a>Binden von Daten an Steuerelemente in einem Aktionsbereich  
 Die Steuerelemente im Aktionsbereich haben die gleichen Datenbindungsfunktionen wie Steuerelemente in Windows Forms. Sie können die Steuerelemente an Datenquellen wie Datasets, typisierte Datasets und XML binden. Weitere Informationen finden Sie unter [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 Sie können Steuerelemente im Aktionsbereich und Steuerelemente im Dokument an das gleiche Dataset binden. Beispielsweise können Sie eine Master-/Detailbeziehung zwischen den Steuerelementen im Aktionsbereich und den Steuerelementen im Arbeitsblatt erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## <a name="validating-data-in-actions-pane-controls"></a>Überprüfen von Daten in Aktionsbereich-Steuerelementen  
 Wenn Sie ein Meldungsfeld im <xref:System.Windows.Forms.Control.Validating>-Ereignishandler eines Steuerelements im Aktionsbereich anzeigen, kann das Ereignis ein zweites Mal ausgelöst werden, wenn sich der Fokus vom Steuerelement auf das Meldungsfeld verlagert. Um dies zu verhindern, verwenden Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement zum Anzeigen von Überprüfungsfehlermeldungen.  
  
## <a name="user-control-stacking-order"></a>Stapelreihenfolge von Benutzersteuerelementen  
 Wenn Sie mehrere Benutzersteuerelemente verwenden, können Sie Code schreiben, durch den die Benutzersteuerelemente im Aktionsbereich – ob vertikal oder horizontal angedockt – richtig gestapelt werden. Sie können die Stapelreihenfolge der Benutzersteuerelemente im Aktionsbereich mithilfe der <xref:Microsoft.Office.Tools.StackStyle>-Enumeration der <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 Die <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft akzeptiert die folgenden <xref:Microsoft.Office.Tools.StackStyle>-Enumerationswerte.  
  
|Stapelstil|Definition|  
|--------------------|----------------|  
|FromBottom|Stapelt vom unteren Rand des Aktionsbereichs.|  
|FromLeft|Stapelt vom linken Rand des Aktionsbereichs.|  
|FromRight|Stapelt vom rechten Rand des Aktionsbereichs.|  
|FromTop|Stapelt von oberen Rand des Aktionsbereichs.|  
|Keine|Es wurde keine Stapelreihenfolge definiert; die Reihenfolge wird vom Entwickler gesteuert.|  
  
 Im folgenden Code wird die <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>-Eigenschaft festgelegt, um die Benutzersteuerelemente vom oberen Rand des Aktionsbereichs zu stapeln.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  
  
## <a name="anchoring-controls"></a>Verankern von Steuerelementen  
 Wenn der Benutzer die Größe des Aktionsbereichs zur Laufzeit ändert, kann sich die Größe der Steuerelemente mit dem Aktionsbereich ändern. Sie können die <xref:System.Windows.Forms.Control.Anchor%2A>-Eigenschaft eines Windows Forms-Steuerelements verwenden, um Steuerelemente im Aktionsbereich zu verankern. Auf dieselbe Weise können Sie auch die Windows Forms-Steuerelemente im Benutzersteuerelement verankern. Weitere Informationen finden Sie unter [wie: Verankern von Steuerelementen in Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
## <a name="resizing-the-actions-pane"></a>Ändern der Größe des Aktionsbereichs  
 Sie können die Größe von <xref:Microsoft.Office.Tools.ActionsPane> nicht direkt ändern, weil <xref:Microsoft.Office.Tools.ActionsPane> in den Aufgabenbereich eingebettet ist. Sie können die Breite des Aufgabenbereichs jedoch programmgesteuert ändern, indem Sie die <xref:Microsoft.Office.Core.CommandBar.Width%2A>-Eigenschaft der <xref:Microsoft.Office.Core.CommandBar> festlegen, die den Aufgabenbereich darstellt. Sie können die Höhe des Aufgabenbereichs ändern, falls er horizontal angedockt oder unverankert ist.  
  
 Das programmgesteuerte Ändern der Größe des Aufgabenbereichs wird im Allgemeinen nicht empfohlen, da der Benutzer in der Lage sein sollte, die Größe des Aufgabenbereichs gemäß seinen individuellen Anforderungen auszuwählen. Wenn Sie die Breite des Aufgabenbereichs jedoch ändern müssen, können Sie für diese Aufgabe den folgenden Code verwenden.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  
  
## <a name="repositioning-the-actions-pane"></a>Neupositionieren des Aktionsbereichs  
 Sie können den <xref:Microsoft.Office.Tools.ActionsPane> nicht direkt neu positionieren, da er in den Aufgabenbereich eingebettet ist. Sie können den Aufgabenbereich jedoch programmgesteuert verschieben, indem Sie die <xref:Microsoft.Office.Core.CommandBar.Position%2A>-Eigenschaft der <xref:Microsoft.Office.Core.CommandBar> festlegen, die den Aufgabenbereich darstellt.  
  
 Das programmgesteuerte Neupositionieren des Aufgabenbereichs wird im Allgemeinen nicht empfohlen, da der Benutzer in der Lage sein sollte, den Aufgabenbereichs gemäß seinen individuellen Anforderungen zu positionieren. Wenn Sie den Aufgabenbereich jedoch verschieben müssen, können Sie für diese Aufgabe den folgenden Code verwenden.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Endbenutzer können den Aufgabenbereich jederzeit manuell neu positionieren. Es gibt keine Möglichkeit sicherzustellen, dass der Aufgabenbereich an der Position angedockt bleibt, die Sie programmgesteuert festlegen. Allerdings können Sie Änderungen in Bezug auf die Ausrichtung suchen und sicherstellen, dass die Steuerelemente im Aktionsbereich in der richtigen Richtung gestapelt sind. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Durch das Festlegen der <xref:Microsoft.Office.Tools.ActionsPane.Top%2A>-Eigenschaft und der <xref:Microsoft.Office.Tools.ActionsPane.Left%2A>-Eigenschaft von <xref:Microsoft.Office.Tools.ActionsPane> wird dessen Position nicht geändert, da das <xref:Microsoft.Office.Tools.ActionsPane>-Objekt in den Aufgabenbereich eingebettet ist.  
  
 Wenn der Aufgabenbereich nicht angedockt ist, können Sie die <xref:Microsoft.Office.Core.CommandBar.Top%2A>-Eigenschaft und die <xref:Microsoft.Office.Core.CommandBar.Left%2A>-Eigenschaft von <xref:Microsoft.Office.Core.CommandBar> festlegen, der den Aufgabenbereich darstellt. Durch den folgenden Code wird ein nicht angedockter Aufgabenbereich in die obere linke Ecke des Dokuments verschoben.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von WPF-Steuerelementen in Office-Projektmappen](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  