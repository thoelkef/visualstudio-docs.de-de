---
title: "Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten | Microsoft Docs"
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
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fad536f7e9f0891f7630cd86d31cea279d5706f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Gewusst wie: Programmgesteuertes automatisches Füllen von Bereichen mit inkrementellen Daten
  Die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode der <xref:Microsoft.Office.Interop.Excel.Range> Objekt können Sie einen Bereich in einem Arbeitsblatt automatisch mit Werten füllen. In den meisten Fällen die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode zum Speichern von inkrementell erhöhen oder verringern die Werte in einem Bereich verwendet wird. Sie können das Verhalten angeben, indem Sie eine optionale Konstante aus der <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> Enumeration.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie müssen zwei Bereiche angeben, wenn mit <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Der Bereich, der die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode, die die Startposition des Füllvorgangs angegeben und einen Anfangswert enthält.  
  
-   Der Bereich, der zu füllenden, übergeben wird, als Parameter an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode. Dieser Zielbereich muss es sich um den Bereich enthalten, der den anfänglichen Wert enthält.  
  
    > [!NOTE]  
    >  Sie können keine übergeben einer <xref:Microsoft.Office.Tools.Excel.NamedRange> steuern anstelle von der <xref:Microsoft.Office.Interop.Excel.Range>. Weitere Informationen finden Sie unter [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Die erste Zelle des Bereichs, die zu füllende muss es sich um einen Anfangswert enthalten.  
  
 Im Beispiel erfordert, dass Sie drei Bereiche füllen:  
  
-   Spalte B ist auf fünf Wochentage enthalten. Geben Sie für den anfänglichen Wert **Montag** in Zelle B1.  
  
-   Spalte C werden fünf Monate enthalten. Geben Sie für den anfänglichen Wert **Januar** in Zelle C1.  
  
-   D-Spalte besteht darin, eine Reihe von Zahlen, besitzt eine Schrittweite von 2 für jede Zeile enthalten. Geben Sie für die Anfangswerte **4** in Zelle D1 und **6** in Zelle D2.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Ausführen von Excel-Berechnungen programmgesteuert](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  