---
title: "Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen | Microsoft Docs"
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
  - "Arbeitsmappen, Speichern"
  - "Arbeitsmappen, Speichern von Sicherungskopien"
  - "Arbeitsmappen, Speichern im XML-Format"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen
  Es gibt mehrere Möglichkeiten, eine Arbeitsmappe zu speichern.  Sie können eine Arbeitsmappe speichern, ohne den Pfad zu ändern.  Wenn die Arbeitsmappe noch nicht gespeichert wurde, sollten Sie sie unter Angabe eines Pfads speichern.  Ohne expliziten Pfad speichert Microsoft Office Excel die Datei unter dem bei der Erstellung angegebenen Namen im aktuellen Ordner.  Sie können auch eine Kopie der Arbeitsmappe speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Speichern einer Arbeitsmappe, ohne den Pfad zu ändern  
  
#### So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A>\-Methode der ThisWorkbook\-Klasse auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### So speichern Sie die aktive Arbeitsmappe in einem VSTO\-Add\-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>\-Methode auf, um die aktive Arbeitsmappe zu speichern.  Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Speichern einer Arbeitsmappe unter einem neuen Pfad  
 Sie können die angegebene Arbeitsmappe an einem neuen Speicherort oder unter einem neuen Namen speichern und optional ein Dateiformat, ein Kennwort, einen Zugriffsmodus und mehr angeben.  
  
> [!NOTE]  
>  Sie können die <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A>\-Eigenschaft auf **False** festlegen, bevor Sie die Arbeitsmappe unter einem neuen Pfad speichern, da beim Speichern in einigen Formaten eine Interaktion erforderlich ist.  Wenn diese Eigenschaft auf **False** festgelegt wird, verwendet Excel alle Standardeinstellungen.  
  
#### So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>\-Methode der `ThisWorkbook`\-Klasse auf.  Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`\-Klasse aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### So speichern Sie die aktive Arbeitsmappe in einem VSTO\-Add\-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>\-Methode auf, um die aktive Arbeitsmappe unter einem neuen Pfad zu speichern.  Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Speichern einer Kopie der Arbeitsmappe  
 Sie können eine Kopie der Arbeitsmappe in einer Datei speichern, ohne die geöffnete Arbeitsmappe im Arbeitsspeicher zu ändern.  Dies ist hilfreich, wenn Sie eine Sicherungskopie erstellen möchten, ohne den Speicherort der Arbeitsmappe zu ändern.  
  
#### So speichern Sie eine Arbeitsmappe, die einer Anpassung auf Dokumentebene zugeordnet ist  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A>\-Methode der `ThisWorkbook`\-Klasse auf.  Zur Verwendung des folgenden Codebeispiels führen Sie es in der `ThisWorkbook`\-Klasse aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### So speichern Sie die aktive Arbeitsmappe in einem VSTO\-Add\-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>\-Methode auf, um eine Kopie der aktiven Arbeitsmappe zu speichern.  Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Robuste Programmierung  
 Wenn eine der Methoden, mit der die Arbeitsmappe gespeichert oder kopiert wird, interaktiv abgebrochen wird, wird ein Laufzeitfehler im Code ausgelöst.  Wenn die Prozedur beispielsweise die <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>\-Methode aufruft, ohne jedoch Aufforderungen von Excel zu deaktivieren, und der Benutzer nach einer Aufforderung auf **Abbrechen** klickt, löst Excel einen Laufzeitfehler aus.  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  