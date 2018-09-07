---
title: 'Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d545b82c913573a5fbfb8d9397efa9ca672e1896
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673697"
---
# <a name="how-to-programmatically-create-word-tables"></a>Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen
  Die Auflistung <xref:Microsoft.Office.Interop.Word.Tables> ist ein Element der Klassen <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> und <xref:Microsoft.Office.Interop.Word.Range>. Dies bedeutet, dass Sie in jedem dieser Kontexte eine Tabelle erstellen können. Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Tables>, um eine Tabelle im angegebenen Bereich hinzuzufügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Erstellen von Tabellen in Anpassungen auf Dokumentebene  
  
### <a name="to-add-a-table-to-a-document"></a>Um eine Tabelle zu einem Dokument hinzuzufügen.  
  
-   Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>, um eine Tabelle am Anfang des Dokuments hinzufügen, die aus drei Zeilen und vier Spalten besteht.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 Wenn Sie eine Tabelle erstellen, wird diese der Auflistung <xref:Microsoft.Office.Interop.Word.Tables> des <xref:Microsoft.Office.Tools.Word.Document>-Hostelements automatisch hinzugefügt . Sie können dann auf die Tabelle über ihre Elementnummer verweisen, indem Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> wie im folgenden Code gezeigt verwenden.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>So verweisen Sie auf eine Tabelle über die Artikelnummer  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, und stellen Sie die Elementnummer der Tabelle bereit, auf die Sie verweisen möchten.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Jedes <xref:Microsoft.Office.Interop.Word.Table>-Objekt verfügt außerdem über eine Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, die das Festlegen von Formatierungsattributen ermöglicht.  
  
### <a name="to-apply-a-style-to-a-table"></a>So wenden Sie eine Formatvorlage auf eine Tabelle an  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Style%2A>, um eine der integrierten Word-Formatvorlagen auf eine Tabelle anzuwenden.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>Erstellen von Tabellen in VSTO-Add-ins  
  
### <a name="to-add-a-table-to-a-document"></a>Um eine Tabelle zu einem Dokument hinzuzufügen.  
  
-   Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>, um eine Tabelle am Anfang des Dokuments hinzufügen, die aus drei Zeilen und vier Spalten besteht.  
  
     Im folgenden Codebeispiel wird dem aktiven Dokument eine Tabelle hinzugefügt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 Wenn Sie eine Tabelle erstellen, wird diese der Auflistung <xref:Microsoft.Office.Interop.Word.Tables> des <xref:Microsoft.Office.Interop.Word.Document>-Objekts automatisch hinzugefügt . Sie können dann auf die Tabelle über ihre Elementnummer verweisen, indem Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> wie im folgenden Code gezeigt verwenden.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>So verweisen Sie auf eine Tabelle über die Artikelnummer  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, und stellen Sie die Elementnummer der Tabelle bereit, auf die Sie verweisen möchten.  
  
     Im folgenden Codebeispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Jedes <xref:Microsoft.Office.Interop.Word.Table>-Objekt verfügt außerdem über eine Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, die das Festlegen von Formatierungsattributen ermöglicht.  
  
### <a name="to-apply-a-style-to-a-table"></a>So wenden Sie eine Formatvorlage auf eine Tabelle an  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Style%2A>, um eine der integrierten Word-Formatvorlagen auf eine Tabelle anzuwenden.  
  
     Im folgenden Codebeispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Programmgesteuertes Hinzufügen von Text und Formatierungen zu Zellen in Word-Tabellen](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  