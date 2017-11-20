---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Arbeitsmappen | Microsoft Docs'
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
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5be604d75183209ecdf068409e26007277cb6d98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-workbooks"></a>Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen
  Es gibt mehrere Möglichkeiten, eine Arbeitsmappe zu speichern. Sie können eine Arbeitsmappe speichern, ohne den Pfad zu ändern. Wenn die Arbeitsmappe noch nicht gespeichert wurde, sollten Sie sie unter Angabe eines Pfads speichern. Ohne expliziten Pfad speichert Microsoft Office Excel die Datei unter dem bei der Erstellung angegebenen Namen im aktuellen Ordner. Sie können auch eine Kopie der Arbeitsmappe speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>Speichern einer Arbeitsmappe, ohne den Pfad zu ändern  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A>-Methode der ThisWorkbook-Klasse auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>-Methode auf, um die aktive Arbeitsmappe zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>Speichern einer Arbeitsmappe unter einem neuen Pfad  
 Sie können die angegebene Arbeitsmappe an einem neuen Speicherort oder unter einem neuen Namen speichern und optional ein Dateiformat, ein Kennwort, einen Zugriffsmodus und mehr angeben.  
  
> [!NOTE]  
>  Möglicherweise möchten Sie legen die <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> Eigenschaft, um **"false"** , bevor die Arbeitsmappe unter einem neuen Pfad speichern, da beim Speichern in einigen Formaten eine Interaktion erforderlich ist. Wenn diese Eigenschaft auf **"false"** bewirkt, dass Excel alle Standardeinstellungen verwendet.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>-Methode der `ThisWorkbook`-Klasse auf. Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`-Klasse aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>-Methode auf, um die aktive Arbeitsmappe unter einem neuen Pfad zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>Speichern einer Kopie der Arbeitsmappe  
 Sie können eine Kopie der Arbeitsmappe in einer Datei speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern. Dies ist hilfreich, wenn Sie eine Sicherungskopie erstellen möchten, ohne den Speicherort der Arbeitsmappe zu ändern.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A>-Methode der `ThisWorkbook`-Klasse auf. Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`-Klasse aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>So speichern Sie die aktive Arbeitsmappe in einem VSTO-Add-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>-Methode auf, um eine Kopie der aktiven Arbeitsmappe zu speichern. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`-Klasse in einem VSTO-Add-In-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn eine der Methoden, mit der die Arbeitsmappe gespeichert oder kopiert wird, interaktiv abgebrochen wird, wird ein Laufzeitfehler im Code ausgelöst. Z. B., wenn die Prozedur aufruft der <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> -Methode, aber nicht deaktivieren von Excel aufforderungen, verfügt und die benutzeraufrufen **"Abbrechen"** Aufforderung, löst Excel einen Laufzeitfehler aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  