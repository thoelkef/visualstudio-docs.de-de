---
title: 'Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f6e9bea3d45249d847f2dccfe522f832d6a07b5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644522"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument
  Wenn Sie Daten, für den Datencache in einem Dokument oder die Arbeitsmappe, die mit einem Kennwort geschützt ist hinzufügen, werden Änderungen an den zwischengespeicherten Daten nicht automatisch gespeichert. Sie können Änderungen an den zwischengespeicherten Daten durch Überschreiben der Methoden in Ihrem Projekt speichern.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Zwischenspeichern in Word-Dokumenten

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Zum Zwischenspeichern von Daten in einem Worddokument, das mit einem Kennwort geschützt ist

1.  In der `ThisDocument` Klasse fest, markieren Sie ein öffentliches Feld oder Eigenschaft, die zwischengespeichert werden. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).

2.  Überschreiben der <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> -Methode in der die `ThisDocument` Klasse, und Entfernen des Schutzes vom Dokument.

     Wenn das Dokument gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode zum Schutz des Dokuments aufgehoben werden kann. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden soll.

3.  Überschreiben der <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> -Methode in der die `ThisDocument` Klasse, und wenden Sie Schutz für das Dokument erneut an.

     Nachdem das Dokument gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode zum Schutz des Dokuments erneut angewendet werden kann.

### <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Zwischenspeichern von Daten in einem Word-Dokument, das mit einem Kennwort geschützt ist. Bevor der Code entfernt. der Schutz von in werden die <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> -Methode, speichert die aktuelle <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> Wert so, dass die gleiche Art von Schutz im erneut angewendet werden kann die <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> Methode.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Kompilieren des Codes
 Fügen Sie folgenden Code, der `ThisDocument` Klasse im Projekt. Dieser Code setzt voraus, dass das Kennwort, in einem Feld namens gespeichert wird `securelyStoredPassword`.

## <a name="cache-in-excel-workbooks"></a>Zwischenspeichern in Excel-Arbeitsmappen
 In Excel-Projekten, dieses Verfahren ist erforderlich, nur, wenn Sie die gesamte Arbeitsmappe mit einem Kennwort schützen, mit der <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> Methode. Dieses Verfahren ist nicht erforderlich, wenn Sie nur eine bestimmte Arbeitsmappe mit einem Kennwort schützen, mit der <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> Methode.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Zum Zwischenspeichern von Daten in einer Excel-Arbeitsmappe, die mit einem Kennwort geschützt ist

1.  In der `ThisWorkbook` Klasse oder eines der `Sheet` *n* Klassen, markieren Sie ein öffentliches Feld oder Eigenschaft, die zwischengespeichert werden. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).

2.  Überschreiben der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> -Methode in der die `ThisWorkbook` Klasse, und Entfernen des Schutzes aus der Arbeitsmappe.

     Wenn die Arbeitsmappe gespeichert wird, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode zum Schutz die Arbeitsmappe aufgehoben werden kann. Dadurch können Änderungen an den zwischengespeicherten Daten gespeichert werden soll.

3.  Überschreiben der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> -Methode in der die `ThisWorkbook` Klasse, und wenden Sie Schutz für das Dokument erneut an.

     Nach dem Speichern der Arbeitsmappe die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ruft diese Methode zum Schutz der Arbeitsmappe wieder aktiviert werden kann.

### <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Daten in einer Excel-Arbeitsmappe zwischengespeichert, die mit einem Kennwort geschützt ist. Bevor der Code entfernt. der Schutz von in werden die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> -Methode, speichert die aktuelle <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> und <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> Werte, damit die gleiche Art von Schutz im erneut angewendet werden kann die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> Methode.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Kompilieren des Codes
 Fügen Sie folgenden Code, der `ThisWorkbook` Klasse im Projekt. Dieser Code setzt voraus, dass das Kennwort, in einem Feld namens gespeichert wird `securelyStoredPassword`.

## <a name="see-also"></a>Siehe auch
- [Zwischenspeichern von Daten](../vsto/caching-data.md)
- [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
