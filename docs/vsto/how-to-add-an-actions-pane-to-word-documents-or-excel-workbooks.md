---
title: 'Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7c49fcf50046148ca01e2ce4eb5ebb204874d1d0
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648238"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen
  Um ein Microsoft Office Word-Dokument oder einer Microsoft Excel-Arbeitsmappe einen Aktionsbereich hinzuzufügen, müssen Sie zuerst erstellen Sie ein Windows Forms-Benutzersteuerelement. Anschließend fügen das Benutzersteuerelement, um die <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> Eigenschaft der `ThisDocument.ActionsPane` Feld (Wort) oder `ThisWorkbook.ActionsPane` Feld (Excel) in Ihrem Projekt.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Erstellen des Benutzersteuerelements  
 Das folgende Verfahren zeigt, wie Benutzersteuerelemente in einem Word oder Excel-Projekt. Es fügt auch eine Schaltfläche auf das Benutzersteuerelement, das Text in das Dokument oder Arbeitsmappe schreibt, wenn darauf geklickt wird.  
  
#### <a name="to-create-the-user-control"></a>Um das Benutzersteuerelement zu erstellen.  
  
1.  Öffnen Sie Ihr Projekt für Word oder Excel auf Dokumentebene in Visual Studio.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Aktionsbereich-Steuerelements**, nennen Sie sie **HelloControl**, und klicken Sie auf **hinzufügen**.  
  
    > [!NOTE]  
    >  Sie können alternativ Hinzufügen einer **Benutzersteuerelement** Element zu Ihrem Projekt. Die Klassen generiert, indem die **Aktionsbereich-Steuerelements** und **Benutzersteuerelement** Elemente sind funktional äquivalent.  
  
4.  Von der **Windows Forms** Registerkarte die **Toolbox** ziehen Sie eine **Schaltfläche** Steuerelement auf das Steuerelement.  
  
    > [!NOTE]  
    >  Wenn das Steuerelement nicht im Designer angezeigt wird, doppelklicken klicken Sie auf **HelloControl** in **Projektmappen-Explorer**.  
  
5.  Fügen Sie den Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler der Schaltfläche. Das folgende Beispiel zeigt Code für Microsoft Office Word-Dokument.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  In c# müssen Sie einen Ereignishandler für das Schaltflächen-Klickereignis hinzufügen. Sie können diesen Code in Platzieren der `HelloControl` Konstruktor nach dem Aufruf von `InitializeComponent`.  
  
     Weitere Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Fügen Sie das Benutzersteuerelement, um den Bereich "Aktionen"  
 Fügen Sie das Benutzersteuerelement, um den Bereich "Aktionen" anzuzeigen, die <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> Eigenschaft der `ThisDocument.ActionsPane` Feld (Word) oder `ThisWorkbook.ActionsPane` Feld (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Der Bereich "Aktionen" das Benutzersteuerelement hinzu  
  
1.  Fügen Sie den folgenden Code der `ThisDocument` oder `ThisWorkbook` Klasse als eine Deklaration auf Klassenebene (Fügen Sie diesen Code nicht an eine Methode).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Fügen Sie den folgenden Code der `ThisDocument_Startup` -Ereignishandler des der `ThisDocument` Klasse oder die `ThisWorkbook_Startup` -Ereignishandler des der `ThisWorkbook` Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  