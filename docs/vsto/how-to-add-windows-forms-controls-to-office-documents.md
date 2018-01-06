---
title: "Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten | Microsoft Docs"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2503ab821f22cb04c6f31d4e5174e755d58cab4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten
  Sie können Microsoft Office Excel- und Microsoft Office Word-Dokumenten Windows Forms-Steuerelemente in Projekten auf Dokumentebene zur Entwurfszeit hinzufügen. Zur Laufzeit können Sie Steuerelemente in Anpassungen auf Dokumentebene und in VSTO-Add-Ins hinzufügen. Sie können Ihrem Arbeitsblatt z. B. ein <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox>-Steuerelement hinzufügen, um den Benutzern die Auswahl aus einer Liste von Optionen zu ermöglichen.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von Steuerelementen zur Laufzeit in Projekten auf Dokumentebene](#runtimedoclevel)  
  
-   [Hinzufügen von Steuerelementen zur Laufzeit in VSTO-Add-ins](#runtimeaddin)  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie: Hinzufügen von Steuerelementen zu einer Dokumentoberfläche zur Laufzeit?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a>Hinzufügen von Steuerelementen zur Entwurfszeit  
 Es gibt mehrere Möglichkeiten, dem Dokument Windows Forms-Steuerelemente in einem Projekt auf Dokumentebene zur Entwurfszeit hinzuzufügen.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-drag-a-windows-forms-control-to-the-document"></a>So ziehen ein Windows Forms-Steuerelement auf das Dokument  
  
1.  Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, klicken Sie auf das Steuerelement, das Sie hinzufügen möchten, und ziehen Sie es in das Dokument.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### <a name="to-draw-a-windows-forms-control-on-the-document"></a>So ziehen ein Windows Forms-Steuerelement auf das Dokument  
  
1.  Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, klicken Sie auf das Steuerelement, das Sie hinzufügen möchten.  
  
3.  Klicken Sie im Dokument auf die Stelle, an der die linke obere Ecke des Steuerelements positioniert werden soll, und ziehen Sie den Mauszeiger an die Stelle, an der sich die untere rechte Ecke des Steuerelements befinden soll.  
  
     Das Steuerelement wird dem Dokument mit der angegebenen Größe und Position hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, sehen Sie **=EMBED("WinForms.Control.Host","")** in der **Bearbeitungsleiste**. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement durch einfaches Klicken auf das Steuerelement hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, klicken Sie auf das Steuerelement, das Sie hinzufügen möchten.  
  
3.  Klicken Sie im Dokument auf die Stelle, an der das Steuerelement hinzugefügt werden soll.  
  
     Das Steuerelement wird dem Dokument mit der Standardgröße hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement durch Doppelklicken auf das Steuerelement hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, doppelklicken Sie auf das Steuerelement, das Sie hinzufügen möchten.  
  
     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>So fügen Sie dem Dokument ein Windows Forms-Steuerelement durch Drücken der EINGABETASTE hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel-Arbeitsmappen- oder Word-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, klicken Sie auf das Steuerelement, das Sie hinzufügen möchten, und drücken Sie die EINGABETASTE.  
  
     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
##  <a name="runtimedoclevel"></a>Hinzufügen von Steuerelementen zur Laufzeit in Projekten auf Dokumentebene  
 Sie können einem Dokument Windows Forms-Steuerelemente zur Laufzeit programmgesteuert hinzufügen. Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A>-Eigenschaft der `ThisDocument`-Klasse. Verwenden Sie in Excel die Methoden der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> Eigenschaft eine `Sheet`  *n*  Klasse. Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.  
  
 Wenn Sie einem Dokument ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird. Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen. Weitere Informationen finden Sie unter [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>So fügen Sie ein Windows Forms-Steuerelement zur Laufzeit hinzu  
  
1.  Verwenden Sie eine Methode mit dem Namen hinzufügen\<*Steuerelementklasse*> (, in denen *Steuerelementklasse* ist der Klassenname des Windows Forms-Steuerelements, das Sie hinzufügen z. B., möchten <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Das folgende Codebeispiel veranschaulicht das Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.Controls.Button> Zelle **C5** von `Sheet1` in einem Projekt auf Dokumentebene für Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a>Hinzufügen von Steuerelementen zur Laufzeit in VSTO-Add-ins  
 Sie können einem beliebigen geöffneten Dokument zur Laufzeit Windows Forms-Steuerelemente hinzufügen. Generieren Sie zuerst ein Hostelement, das auf einem geöffneten Dokument oder Arbeitsblatt basiert. Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>-Eigenschaft des neuen Hostelements. Verwenden Sie in Excel die Methoden der <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>-Eigenschaft des neuen Hostelements. Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.  
  
 Wenn Sie einem Dokument ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird. Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen. Weitere Informationen finden Sie unter [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Weitere Informationen zum Generieren von Hostelementen in VSTO-Add-in-Projekten finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-windows-forms-control-at-run-time"></a>So fügen Sie ein Windows Forms-Steuerelement zur Laufzeit hinzu  
  
1.  Verwenden Sie eine Methode mit dem Namen hinzufügen\<*Steuerelementklasse*> (, in denen *Steuerelementklasse* ist der Klassenname des Windows Forms-Steuerelements, das Sie hinzufügen z. B., möchten <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  In VSTO-Add-in-Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher müssen Sie einen Verweis auf die Assembly Microsoft.Office.Tools.Excel.v4.0.Utilities.dll oder Microsoft.Office.Tools.Word.v4.0.Utilities.dll hinzufügen, bevor Sie die Add zugreifen können\< *Steuerelementklasse*> Methoden.  
  
     Das folgende Codebeispiel veranschaulicht das Hinzufügen von <xref:Microsoft.Office.Tools.Word.Controls.Button> im ersten Absatz des aktiven Dokuments mithilfe eines Word-VSTO-Add-Ins.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  