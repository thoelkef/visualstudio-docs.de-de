---
title: 'Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ee790707a5c1c74f3227f74874c66bb4438e7ab0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991174"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen
  Ein Bereich "Aktionen" wird rechts neben einem Dokument oder Arbeitsblatt standardmäßig angedockt werden; Sie können jedoch auf die Links, oben oder unten angedockt werden. Wenn Sie mehrere Benutzersteuerelemente verwenden, können Sie Code aus, um ordnungsgemäß die Benutzersteuerelemente im Aktionsbereich gestapelt schreiben. Weitere Informationen finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Stapelreihenfolge der Steuerelemente hängt davon ab, ob der Bereich "Aktionen" vertikal oder horizontal angedockt ist.  
  
> [!NOTE]  
>  Wenn der Benutzer den Bereich "Aktionen", zur Laufzeit angepasst wird, können Sie die Steuerelemente mit dem Aktionsbereich Ändern der Größe festlegen. Sie können die <xref:System.Windows.Forms.Control.Anchor%2A>-Eigenschaft eines Windows Forms-Steuerelements verwenden, um Steuerelemente im Aktionsbereich zu verankern. Weitere Informationen finden Sie unter [Vorgehensweise: Verankern von Steuerelementen in Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Die Stack-Reihenfolge der Steuerelemente im Bereich Aktionen festlegen  
  
1.  Öffnen Sie ein Projekt auf Dokumentebene für Microsoft Office Word, die einen Aktionsbereich mehrere Benutzersteuerelemente oder geschachtelte Aktionsbereich-Steuerelementen enthält. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Mit der rechten Maustaste **ThisDocument.cs** oder **ThisDocument.vb** in **Projektmappen-Explorer** , und klicken Sie dann auf **Ansichtscode**.  
  
3.  In der <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> -Ereignishandler des Aktionsbereichs, überprüfen Sie, ob der Aktionsbereich horizontal ausgerichtet ist.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Bei horizontal ausgerichtet ist, stapeln Sie die Aktion-Steuerelemente aus der linken Seite. andernfalls Stapeln von oben.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  In c# müssen Sie einen Ereignishandler für Hinzufügen der `ActionsPane` auf die <xref:Microsoft.Office.Tools.Word.Document.Startup> -Ereignishandler. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Führen Sie das Projekt, und stellen Sie sicher, dass das Aktionsbereich-Steuerelement von links nach rechts gestapelt sind, wenn der Bereich "Aktionen" am oberen Rand des Dokuments angedockt ist, und die Steuerelemente werden von oben nach unten gestapelt, wenn der Bereich "Aktionen" auf der rechten Seite des Dokuments angedockt wird.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Ein Wort auf Dokumentebene-Projekt mit einem Bereich "Aktionen", die mehrere Benutzersteuerelemente enthält oder geschachtelte Aktionsbereich steuert.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Vorgehensweise: Hinzufügen von Aktionen im Bereich zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
