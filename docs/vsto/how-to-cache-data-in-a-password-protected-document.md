---
title: "Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument | Microsoft Docs"
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
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ecc4913d9d508d95347945b8f4aaa816bc3d510c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Gewusst wie: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument
  Wenn Sie Daten, für den Datencache in ein Dokument oder eine Arbeitsmappe, die mit einem Kennwort geschützt ist hinzufügen, werden Änderungen an den zwischengespeicherten Daten nicht automatisch gespeichert. Sie können die zwischengespeicherten Daten Änderungen speichern, durch Überschreiben der beiden Methoden in Ihrem Projekt.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Zwischenspeichern in Word-Dokumenten  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Zum Zwischenspeichern von Daten in einem Worddokument, die mit einem Kennwort geschützt ist  
  
1.  In der `ThisDocument` -Klasse, markieren Sie ein öffentliches Feld oder eine Eigenschaft, die zwischengespeichert werden soll. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).  
  
2.  Überschreiben der <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> Methode in der `ThisDocument` Klasse, und entfernen Sie den Schutz aus dem Dokument.  
  
     Wenn das Dokument gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode, um Sie zu den Dokumentschutz ermöglichen. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden sollen.  
  
3.  Überschreiben der <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> Methode in der `ThisDocument` Klasse, und wenden Sie Schutz auf das Dokument erneut an.  
  
     Nachdem das Dokument gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode, um das Dokument Schutz wieder aktiviert werden können.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Zwischenspeichern von Daten in einem Word-Dokument, die mit einem Kennwort geschützt ist. Bevor der Code für den Schutz in entfernt die <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> Methode speichert den aktuellen <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> Wert, sodass dieselbe Art von Schutz in erneut angewendet werden kann die <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> Methode.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Kompilieren des Codes  
 Fügen Sie diesen Code, um die `ThisDocument` -Klasse im Projekt. Mit diesem Code wird davon ausgegangen, dass das Kennwort in einem Feld namens gespeichert ist `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>Zwischenspeichern in Excel-Arbeitsmappen  
 In Excel-Projekten, diese Vorgehensweise ist erforderlich, nur, wenn Sie die gesamte Arbeitsmappe mit einem Kennwort, mithilfe Schützen der <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> Methode. Dieses Verfahren ist nicht erforderlich, wenn Sie nur eine bestimmte Arbeitsmappe mit einem Kennwort, mithilfe Schützen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> Methode.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Zum Zwischenspeichern von Daten in einer Excel-Arbeitsmappe, die mit einem Kennwort geschützt ist  
  
1.  In der `ThisWorkbook` Klasse oder eines der `Sheet`  *n*  Klassen, markieren Sie ein öffentliches Feld oder eine Eigenschaft, die zwischengespeichert werden soll. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).  
  
2.  Überschreiben der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> Methode in der `ThisWorkbook` -Klasse und Aufheben des Schutzes für die Arbeitsmappe.  
  
     Wenn die Arbeitsmappe gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode, um den Schutz der Arbeitsmappe werden können. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden sollen.  
  
3.  Überschreiben der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> Methode in der `ThisWorkbook` Klasse, und wenden Sie Schutz auf das Dokument erneut an.  
  
     Nachdem die Arbeitsmappe gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode zum Schutz der Arbeitsmappe wieder aktiviert werden können.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Zwischenspeichern von Daten in einer Excel-Arbeitsmappe, die mit einem Kennwort geschützt ist. Bevor der Code für den Schutz in entfernt die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> Methode speichert den aktuellen <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> und <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> Werte, sodass dieselbe Art von Schutz in erneut angewendet werden kann die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> Methode.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Kompilieren des Codes  
 Fügen Sie diesen Code, um die `ThisWorkbook` -Klasse im Projekt. Mit diesem Code wird davon ausgegangen, dass das Kennwort in einem Feld namens gespeichert ist `securelyStoredPassword`.  
  
## <a name="see-also"></a>Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung Offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  