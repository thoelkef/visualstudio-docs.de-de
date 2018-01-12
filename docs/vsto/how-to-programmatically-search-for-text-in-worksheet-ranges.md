---
title: 'Vorgehensweise: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen | Microsoft Docs'
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 42c95ab26437ad590d457ad926db6e070a7c8de0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen
  Die <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Methode der <xref:Microsoft.Office.Interop.Excel.Range> Objekt können Sie nach Text innerhalb des Bereichs zu suchen. Dieser Text kann die Fehlerzeichenfolgen, die in einer Arbeitsblattzelle wie auch sein `#NULL!` oder `#VALUE!`. Weitere Informationen zu Fehlerzeichenfolgen, finden Sie unter [Zellenfehlerwerte](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgende Beispiel durchsucht einen Bereich, der mit dem Namen `Fruits` und ändert die Schriftart für Zellen, die das Wort "Äpfel" enthalten. Dieses Verfahren auch verwendet die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Methode, die die zuvor festgelegten verwendet Suchen Sie die Einstellungen für die Suche wiederholen. Sie geben die Zelle nach dem gesucht werden soll, und die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> -Methode übernimmt den Rest.  
  
> [!NOTE]  
>  Die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> -Methode umschließt zurück an den Anfang des Suchbereichs das Ende des Bereichs erreicht wurde. Codes muss sicherstellen, dass die Suche in einer Endlosschleife. Die Beispielprozedur zeigt eine Möglichkeit, mithilfe der <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Eigenschaft.  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [How Do I: Use Find-Methode in einem Excel-Add-in?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Zum Suchen nach Text in einem Arbeitsblattbereich  
  
1.  Deklarieren Sie Variablen für das Nachverfolgen von den gesamten Bereich, den ersten gefundenen Bereich und den aktuellen Bereich gefunden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Suchen Sie nach der ersten Übereinstimmung, geben Sie die Parameter für die mit Ausnahme der Zelle, nach dem gesucht werden soll.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Weitersuchen Sie als Übereinstimmungen vorhanden sind.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Vergleichen Sie den ersten gefundenen Bereich (`firstFind`) zu **nichts**. Wenn `firstFind` enthält keinen Wert, den Code gespeichert gefundenen Bereichs (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Die Schleife zu beenden, wenn die Adresse des Bereichs gefunden wurde die Adresse des ersten gefundenen Bereichs übereinstimmt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Festlegen der Darstellung des Bereichs gefunden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Führen Sie eine andere Suche.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 Das folgende Beispiel zeigt die vollständige Methode.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  