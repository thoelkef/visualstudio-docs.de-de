---
title: 'Vorgehensweise: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ae27f4e24ac367741bcdf2dfa2bae8598c6c7d99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865608"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Vorgehensweise: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen
  Wenn Sie suchen und Ersetzen von Text in einem Dokument, empfiehlt es sich um die ursprüngliche Auswahl des Benutzers wiederhergestellt werden, nachdem die Suche abgeschlossen ist.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Der Code in die Beispielprozedur verwendet zwei <xref:Microsoft.Office.Interop.Word.Range> Objekte. Eine speichert die aktuelle <xref:Microsoft.Office.Interop.Word.Selection>, und eine legt das gesamte Dokument als Suchbereich verwendet.  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>Zum Wiederherstellen der ursprünglichen Auswahl des Benutzers nach einer Suche  
  
1. Erstellen der <xref:Microsoft.Office.Interop.Word.Range> Objekte für das Dokument und die aktuelle Auswahl.  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. Führen Sie die Suche, und der Ersetzungsvorgang ist.  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. Wählen Sie den Start-Bereich zum Wiederherstellen der ursprünglichen Auswahl des Benutzers.  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   Das folgende Beispiel zeigt die vollständige Methode.  
  
## <a name="example"></a>Beispiel  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Vorgehensweise: Programmgesteuertes durchlaufen Sie gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
