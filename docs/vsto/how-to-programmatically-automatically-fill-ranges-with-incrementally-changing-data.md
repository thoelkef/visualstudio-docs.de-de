---
title: "Gewusst wie: Programmgesteuertes automatisches F&#252;llen von Bereichen mit inkrementellen Daten | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Autofill-Methode [Excel]"
  - "Füllen von Bereichen (automatisch)"
  - "Bereiche, Automatisches Füllen"
  - "Arbeitsmappen, Füllen von Bereichen"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Gewusst wie: Programmgesteuertes automatisches F&#252;llen von Bereichen mit inkrementellen Daten
  Mit der <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode des <xref:Microsoft.Office.Interop.Excel.Range>\-Objekts können Sie einen Bereich in einem Arbeitsblatt automatisch mit Werten füllen.  Die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode wird hauptsächlich zum Speichern von inkrementell aufsteigenden bzw. absteigenden Werten in einem Bereich verwendet.  Sie können das Verhalten festlegen, indem Sie eine optionale Konstante aus der <xref:Microsoft.Office.Interop.Excel.XlAutoFillType>\-Enumeration angeben.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie müssen zwei Bereiche angeben, wenn Sie <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> verwenden:  
  
-   Den die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode aufrufenden Bereich, der den Ausgangspunkt für den Füllvorgang festlegt und einen Anfangswert enthält.  
  
-   Der Bereich, den Sie füllen möchten, und der als Parameter an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode übergeben wird.  Dieser Zielbereich muss den Bereich einschließen, der den Anfangswert enthält.  
  
    > [!NOTE]  
    >  Sie können kein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement anstelle von <xref:Microsoft.Office.Interop.Excel.Range> übergeben.  Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## Kompilieren des Codes  
 Die erste Zelle des zu füllenden Bereichs muss einen Anfangswert enthalten.  
  
 Das Beispiel erfordert, dass Sie drei Bereiche füllen:  
  
-   Spalte B soll fünf Wochentage enthalten.  Geben Sie in Zelle B1 **Montag** als Anfangswert ein.  
  
-   Spalte C soll fünf Monate enthalten.  Geben Sie in Zelle C1 **Januar** als Anfangswert ein.  
  
-   Spalte D muss Zahlenfolgen enthalten, die in jeder Zeile um zwei zunehmen.  Geben Sie als Anfangswerte in Zelle D1 **4** und in Zelle D2 **6** ein.  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  