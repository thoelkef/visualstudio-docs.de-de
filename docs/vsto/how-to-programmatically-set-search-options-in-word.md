---
title: 'Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b02adab3b0ba032a39ce73c08bd287213ef2ffc4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672688"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word
  Es gibt zwei Möglichkeiten zum Festlegen von Suchoptionen für die Auswahl in Microsoft Office Word-Dokumenten:  
  
-   Legen Sie die einzelne Eigenschaften einer <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
-   Verwenden Sie die Argumente der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> -Methode der ein <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-properties-of-a-find-object"></a>Verwenden Sie die Eigenschaften eines Objekts suchen  
 Der folgende Code legt die Eigenschaften einer <xref:Microsoft.Office.Interop.Word.Find> Objekt zum Suchen nach Text innerhalb der aktuellen Auswahl. Beachten Sie, dass die Suchkriterien ein, z.B. bei der Suche vorwärts, umschließen und Text zu suchenden Eigenschaften sind die <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
 Jede der Eigenschaften der Einstellung der <xref:Microsoft.Office.Interop.Word.Find> Objekt ist nicht hilfreich, wenn Sie c#-Code schreiben, da Sie die gleichen Eigenschaften, als Parameter in angeben müssen der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode. In diesem Beispiel wird daher nur die Visual Basic-Code enthält.  
  
### <a name="to-set-search-options-using-a-find-object"></a>Festlegen von Suchoptionen, die mithilfe eines Objekts suchen  
  
1.  Festlegen der Eigenschaften einer <xref:Microsoft.Office.Interop.Word.Find> Objekt, um vorwärts durch eine Auswahl für den Text suchen **finden Sie mir**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="use-execute-method-arguments"></a>Verwenden Sie die Argumente der Execute-Methode  
 Der folgende code verwendet die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode eine <xref:Microsoft.Office.Interop.Word.Find> Objekt zum Suchen nach Text innerhalb der aktuellen Auswahl. Beachten Sie, die die Suchkriterien entsprechen, z. B. Suche vorwärts, Umbruch und Text zu suchenden als Parameter übergeben werden die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode.  
  
### <a name="to-set-search-options-using-execute-method-arguments"></a>Festlegen von Suchoptionen, die mithilfe der Argumente der Execute-Methode  
  
1.  Suchkriterien als Parameter übergeben die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode, um vorwärts durch eine Auswahl für den Text suchen **finden Sie mir**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Gewusst wie: Programmgesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  