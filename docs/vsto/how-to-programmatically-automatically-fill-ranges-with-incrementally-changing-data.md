---
title: 'Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a704fd0cdc18802aff487b5d66b72044303ce2dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895576"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten
  Die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode der <xref:Microsoft.Office.Interop.Excel.Range> -Objekt ermöglicht Ihnen, einen Bereich in einem Arbeitsblatt automatisch mit Werten zu füllen. In den meisten Fällen die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode wird verwendet, um schrittweise erhöhen oder verringern die Werte in einem Bereich zu speichern. Sie können das Verhalten angeben, indem Sie eine optionale Konstante aus der <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> Enumeration.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie müssen zwei Bereiche angeben, bei Verwendung <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Der Bereich, der die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode, die gibt den Ausgangspunkt der Füllung und einen Anfangswert enthält.  
  
-   Der Bereich, die Sie füllen möchten, übergeben wird, als Parameter an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Methode. Dieser Zielbereich muss es sich um den Bereich enthalten, der den ursprünglichen Wert enthält.  
  
    > [!NOTE]  
    >  Sie können keine übergeben eine <xref:Microsoft.Office.Tools.Excel.NamedRange> steuern anstelle von der <xref:Microsoft.Office.Interop.Excel.Range>. Weitere Informationen finden Sie unter [programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Die erste Zelle des Bereichs, die zu füllende muss es sich um einen anfänglichen Wert enthalten.  
  
 Das Beispiel erfordert, dass Sie drei Regionen ausfüllen:  
  
-   Spalte B ist auf fünf Werktage enthalten. Geben Sie für den ersten Wert **Montag** in Zelle B1.  
  
-   Spalte C werden fünf Monate enthalten. Geben Sie für den ersten Wert **Januar** in Zelle C1.  
  
-   D-Spalte ist eine Reihe von Zahlen, besitzt eine Schrittweite von zwei für jede Zeile enthalten. Geben Sie für die Anfangswerte **4** in Zelle D1 und **6** in Zelle D2.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
