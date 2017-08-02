---
title: "Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen"
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
  - "Text [Office-Entwicklung in Visual Studio], Suchen in Arbeitsblättern"
  - "Textsuche, Arbeitsblätter"
  - "Arbeitsblätter, Suchen"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen
  Mit der <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>\-Methode des <xref:Microsoft.Office.Interop.Excel.Range>\-Objekts können Sie innerhalb des Bereichs nach Text suchen.  Dieser Text kann auch aus einer der Fehlerzeichenfolgen bestehen, die in Arbeitsblattzellen wie `#NULL!` oder `#VALUE!` enthalten sind.  Weitere Informationen über Fehlerzeichenfolgen finden Sie unter [Zellenfehlerwerte](HV10038459).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgenden Beispiel wird ein Bereich mit dem Namen `Fruits` durchsucht und die Schriftart der Zellen geändert, die das Wort "apples" enthalten.  Diese Prozedur verwendet auch die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>\-Methode, die bei Wiederholung einer Suche die zuvor festgelegten Sucheinstellungen verwendet.  Sie geben die Zelle an, nach der gesucht werden soll, und die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>\-Methode übernimmt den Rest.  
  
> [!NOTE]  
>  Die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>\-Methode wird am Bereichsanfang erneut gestartet, wenn beim Suchvorgang das Bereichsende erreicht wurde.  Der Code muss jedoch verhindern, dass die Suche in einer Endlosschleife ausgeführt wird.  Dies können Sie, wie in der folgenden Beispielprozedur gezeigt, mithilfe der <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>\-Eigenschaft erreichen.  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie im Thema zur [Verwendung der Find\-Methode in einem Excel\-Add\-In](http://go.microsoft.com/fwlink/?LinkID=130294) \(möglicherweise in englischer Sprache\).  
  
### So suchen Sie nach Text in einem Arbeitsblattbereich  
  
1.  Deklarieren Sie Variablen zum Durchsuchen des gesamten Bereichs, des ersten gefundenen Bereichs und des aktuell gefundenen Bereichs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  Suchen Sie nach der ersten Übereinstimmung, und legen Sie alle Parameter mit Ausnahme der zu suchenden Zellen fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  Setzen Sie die Suche fort, solange Übereinstimmungen gefunden werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  Vergleichen Sie den ersten gefundenen Bereich \(`firstFind`\) mit **Nothing**.  Wenn `firstFind` keinen Wert enthält, wird der gefundene Bereich \(`currentFind`\) durch den Code gespeichert.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  Beenden Sie die Schleife im Code, wenn die Adresse des gefundenen Bereichs mit der Adresse des zuerst gefundenen Bereichs übereinstimmt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  Legen Sie die Darstellung des gefundenen Bereichs fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  Führen Sie eine weitere Suche aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 Im folgenden Beispiel wird die vollständige Methode veranschaulicht.  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  