---
title: 'Vorgehensweise: Programmgesteuertes Festlegen von Suchoptionen in Word | Microsoft Docs'
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa575f8c89e9aea125179c896c35b8ecc775965e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word
  Es gibt zwei Möglichkeiten zum Festlegen von Suchoptionen für die Auswahl in Microsoft Office Word-Dokumenten:  
  
-   Legen Sie die einzelne Eigenschaften einer <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
-   Verwenden von Argumenten, die von der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode eine <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Verwenden die Eigenschaften eines Objekts suchen  
 Der folgende Code legt die Eigenschaften einer <xref:Microsoft.Office.Interop.Word.Find> Objekt zum Suchen nach Text innerhalb der aktuellen Auswahl. Beachten Sie, dass die Suchkriterien entsprechen, z. B. Suche vorwärts, Umbruch und Text zu suchenden Eigenschaften sind die <xref:Microsoft.Office.Interop.Word.Find> Objekt.  
  
 Jede der Eigenschaften der Einstellung der <xref:Microsoft.Office.Interop.Word.Find> Objekt ist nicht hilfreich, wenn Sie C#-Code schreiben, da Sie die gleichen Eigenschaften als Parameter angeben müssen die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode. In diesem Beispiel wird daher nur Visual Basic-Code enthält.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Festlegen von Suchoptionen mithilfe eines Objekts suchen  
  
1.  Festlegen der Eigenschaften eines eine <xref:Microsoft.Office.Interop.Word.Find> Objekt um vorwärts durch eine Auswahl für den Text suchen **finden Sie mich**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Verwenden von Execute Methodenargumente  
 Der folgende code verwendet die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode von einem <xref:Microsoft.Office.Interop.Word.Find> Objekt zum Suchen nach Text innerhalb der aktuellen Auswahl. Beachten Sie, die die Suchkriterien entsprechen, z. B. Suche vorwärts, Umbruch und Text zu suchende, als Parameter übergeben werden die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Festlegen von Suchoptionen mithilfe der Argumente der Execute-Methode  
  
1.  Suchkriterien als Parameter übergeben der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Methode, um vorwärts durch eine Auswahl für den Text suchen **finden Sie mich**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  