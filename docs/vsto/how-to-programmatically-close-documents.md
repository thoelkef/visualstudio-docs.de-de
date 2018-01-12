---
title: "Vorgehensweise: Programmgesteuertes Schließen von Dokumenten | Microsoft Docs"
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
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c7f75f621cd00df4c782d10ee65ad4444024029f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-close-documents"></a>Gewusst wie: Programmgesteuertes Schließen von Dokumenten
  Sie können das aktive Dokument schließen, oder Sie können ein Dokument angeben, das geschlossen werden soll.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="closing-the-active-document"></a>Schließen des aktiven Dokuments  
 Es gibt zwei Verfahren für das Schließen des aktiven Dokuments: eines für Anpassungen auf Dokumentebene und eines für VSTO-Add-Ins.  
  
#### <a name="to-close-the-active-document-in-a-document-level-customization"></a>So schließen Sie das aktive Dokument in einer Anpassung auf Dokumentebene  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Tools.Word.Document.Close%2A> der Klasse `ThisDocument` in Ihrem Projekt auf, um das der Anpassung zugeordnete Dokument zu schließen. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` aus.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> -Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
#### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>So schließen Sie das aktive Dokument in einem VSTO-Add-In  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> der-Eigenschaft <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> auf, um das aktive Dokument zu schließen. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> -Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="closing-a-document-that-you-specify-by-name"></a>Schließen eines namentlich angegebenen Dokuments  
 Das Schließen eines namentlich angegebenen Dokuments erfolgt bei VSTO-Add-Ins und Anpassungen auf Dokumentebene auf die gleiche Weise.  
  
#### <a name="to-close-a-document-that-you-specify-by-name"></a>So schließen Sie ein namentlich angegebenes Dokument  
  
1.  Geben Sie den Namen des Dokuments als Argument für die Auflistung <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> an, und rufen Sie dann die Methode <xref:Microsoft.Office.Interop.Word._Document.Close%2A> auf. Im folgenden Codebeispiel wird davon ausgegangen, dass ein Dokument namens **NewDocument** in Word geöffnet ist.  
  
    > [!NOTE]  
    >  In diesem Beispiel wird der <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> -Wert an den Parameter *SaveChanges* übergeben, um das Dokument ohne Speichern von Änderungen oder Anzeigen einer Benutzeraufforderung zu schließen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  