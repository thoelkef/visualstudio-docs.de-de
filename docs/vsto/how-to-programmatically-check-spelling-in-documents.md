---
title: "Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten | Microsoft Docs"
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
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 357e92235f474392c3bdbe1ac1f19af8c9c1538a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten
  Um die Rechtschreibprüfung in einem Dokument verwenden Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode. Diese Methode gibt einen booleschen Wert, der angibt, ob der angegebene Parameter richtig geschrieben ist.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Zum Durchführen einer Rechtschreibprüfung und Ergebnisse in einem Meldungsfeld angezeigt.  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode und übergeben sie einen Bereich von Text, der auf Rechtschreibfehler überprüfen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  