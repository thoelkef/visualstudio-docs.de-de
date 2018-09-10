---
title: 'Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e916b16caaaa3944fcdf522ffd320198d9972b52
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256717"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten
  Verwenden Sie zum Überprüfen der Rechtschreibung in einem Dokument die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode. Diese Methode gibt einen booleschen Wert, der angibt, ob der angegebene Parameter richtig geschrieben ist.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Überprüfen der Rechtschreibung und Ergebnisse in einem Meldungsfeld anzeigen  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode und übergeben sie einen Textbereich zu prüfen, Rechtschreibfehler. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  