---
title: "Vorgehensweise: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen | Microsoft Docs"
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56d8c3d0c578d2dc13cf65af680bc2fb804f3539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Gewusst wie: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen
  In einer Microsoft Office Word-Tabelle werden die Zellen in Zeilen und Spalten angeordnet. Sie können die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Rows>-Objekts verwenden, um der Tabelle Zeilen hinzuzufügen, und die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Columns>-Objekts, um Spalten hinzuzufügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Beispiele für die Anpassung auf Dokumentebene  
 Die folgenden Codebeispiele können in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie diese Beispiele verwenden möchten, führen Sie den Code von der `ThisDocument`-Klasse im Projekt aus. In diesen Beispielen wird davon ausgegangen, dass das mit der Anpassung verknüpfte Dokument bereits über mindestens eine Tabelle verfügt.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:  
>   
>  -   Word 2013-Dokument  
> -   Word 2013-Vorlage  
> -   Word 2010-Dokument  
> -   Word 2010-Vorlage  
>   
>  Wenn Sie diese Aufgabe einem anderen Typ von Projekt ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Word** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, Zeilen und Spalten zu Tabellen hinzufügen. Weitere Informationen finden Sie unter [wie: Ziel Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Word 2010 Referenz für primäre Interopassemblys](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>So fügen Sie einer Tabelle eine Zeile hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode, um der Tabelle eine Zeile hinzuzufügen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>So fügen Sie einer Tabelle eine Spalte hinzu  
  
1.  Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>-Methode, um alle Spalten mit der gleichen Breite zu formatieren.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Beispiele für das VSTO-Add-In  
 Die folgenden Codebeispiele können in einem VSTO-Add-In verwendet werden. Wenn Sie diese Beispiele verwenden möchten, führen Sie sie von der `ThisAddIn`-Klasse im Projekt aus. In diesen Beispielen wird davon ausgegangen, dass das aktive Dokument bereits über mindestens eine Tabelle verfügt.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe der VSTO-Add-In-Vorlagen für Word erstellen.  
>   
>  Wenn Sie diese Aufgabe einem anderen Typ von Projekt ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Word** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, Zeilen und Spalten zu Tabellen hinzufügen. Weitere Informationen finden Sie unter [wie: Ziel Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Word 2010 Referenz für primäre Interopassemblys](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>So fügen Sie einer Tabelle eine Zeile hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>-Methode, um der Tabelle eine Zeile hinzuzufügen.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>So fügen Sie einer Tabelle eine Spalte hinzu  
  
1.  Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>-Methode, um alle Spalten mit der gleichen Breite zu formatieren.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen von Text und Formatierungen zu Zellen in Word-Tabellen](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Vorgehensweise: Programmgesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  