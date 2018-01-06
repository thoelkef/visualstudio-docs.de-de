---
title: "Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen | Microsoft Docs"
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
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5c383c95d37894aaa49a4a42d2b9a17b9a193f41
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-protect-workbooks"></a>Gewusst wie: Programmgesteuertes Schützen von Arbeitsmappen
  Sie können eine Microsoft Office Excel-Arbeitsmappe schützen, sodass Benutzer können nicht hinzugefügt oder Löschen von Arbeitsblättern, und heben die Arbeitsmappe auch programmgesteuert. Sie können optional ein Kennwort angeben, gibt an, ob die Struktur (damit die Benutzer können keine Arbeitsblätter verschieben) geschützt werden soll, und gibt an, ob die Arbeitsmappe-Fenster, die geschützt werden sollen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Schützen einer Arbeitsmappe wird Benutzer am bearbeiten Zellen nicht beendet werden. Um die Daten zu schützen, müssen Sie die Arbeitsblätter schützen. Weitere Informationen finden Sie unter [wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Die folgenden Codebeispiele verwenden eine Variable, um ein Kennwort enthalten, die vom Benutzer abgerufen werden.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Schützen einer Arbeitsmappe, die Teil einer Anpassung auf Dokumentebene  
  
#### <a name="to-protect-a-workbook"></a>Um eine Arbeitsmappe zu schützen.  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> Methode der Arbeitsmappe und ein Kennwort enthalten. Um das folgende Codebeispiel zu verwenden, führen Sie es in der `ThisWorkbook` -Klasse, nicht in einer Sheet-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Zum Aufheben des Schutzes von einer Arbeitsmappe  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> -Methode auf und übergibt ein Kennwort, wenn es erforderlich ist. Um das folgende Codebeispiel zu verwenden, führen Sie es in der `ThisWorkbook` -Klasse, nicht in einer Sheet-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Schützen eine Arbeitsmappe mit einem Add-in auf Anwendungsebene  
  
#### <a name="to-protect-a-workbook"></a>Um eine Arbeitsmappe zu schützen.  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> Methode der Arbeitsmappe und ein Kennwort enthalten. Dieses Codebeispiel verwendet die aktive Arbeitsmappe. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Zum Aufheben des Schutzes von einer Arbeitsmappe  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> Methode der aktiven Arbeitsmappe, und übergeben Sie ein Kennwort erforderlich. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  