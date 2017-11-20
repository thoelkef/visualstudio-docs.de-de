---
title: "Vorgehensweise: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen | Microsoft Docs"
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
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28468eaba28d36394754b96bdb13727088885ff1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen
  Wenn Sie suchen und Ersetzen von Text in einem Dokument, empfiehlt es sich, die ursprüngliche Auswahl des Benutzers wiederhergestellt, nachdem die Suche abgeschlossen ist.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Der Code in die Beispielprozedur zwei <xref:Microsoft.Office.Interop.Word.Range> Objekte. Eine speichert die aktuelle <xref:Microsoft.Office.Interop.Word.Selection>, und eine legt das gesamte Dokument als Bereich Suche verwenden.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Zum Wiederherstellen der ursprünglichen Auswahl des Benutzers nach einer Suche  
  
1.  Erstellen der <xref:Microsoft.Office.Interop.Word.Range> Objekte für das Dokument und die aktuelle Auswahl.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Führen Sie die Suche, und der Ersetzungsvorgang ist.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Wählen Sie den Start zum Wiederherstellen der ursprünglichen Auswahl des Benutzers.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 Das folgende Beispiel zeigt die vollständige Methode.  
  
## <a name="example"></a>Beispiel  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Vorgehensweise: Programmgesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  