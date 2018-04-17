---
title: 'Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c997fbe764ba355d16def278c9beda8c177faed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften
  Die oben aufgeführten Microsoft Office-Anwendung bieten integrierte Eigenschaften, die mit Dokumenten gespeichert werden. Darüber hinaus können Sie benutzerdefinierte Dokumenteigenschaften erstellen und ändern, falls Sie zusätzliche Informationen mit dem Dokument speichern möchten.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Verwenden Sie die gibt-Eigenschaft eines Dokuments, um mit benutzerdefinierten Eigenschaften zu arbeiten. Verwenden Sie in einem Projekt auf Dokumentebene für Microsoft Office Excel z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> -Eigenschaft der `ThisWorkbook` -Klasse. Verwenden Sie in einem VSTO-Add-In-Projekt für Excel die <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> -Eigenschaft eines <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekts. Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties> -Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty> -Objekten ist. Sie können die `Item`-Eigenschaft der Auflistung verwenden, um eine bestimmte Eigenschaft nach Namen oder Index in der Auflistung abzurufen.  
  
 Das folgende Beispiel veranschaulicht, wie eine benutzerdefinierte Eigenschaft in einer Anpassung auf Dokumentebene für Excel hinzugefügt und ihr ein Wert zugewiesen wird.  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie: Zugreifen auf und Bearbeiten von benutzerdefinierten Dokumenteigenschaften in Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Beispiel  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Beim Versuch, auf die `Value` -Eigenschaft für nicht definierte Eigenschaften zuzugreifen, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Vorgehensweise: Lesen von und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  