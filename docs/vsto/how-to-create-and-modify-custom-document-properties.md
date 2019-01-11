---
title: 'Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0a3dd497bc2c63c58e6072cd48f58cba071ea4f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891588"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften
  Die oben aufgeführten Microsoft Office-Anwendung bieten integrierte Eigenschaften, die mit Dokumenten gespeichert werden. Darüber hinaus können Sie benutzerdefinierte Dokumenteigenschaften erstellen und ändern, falls Sie zusätzliche Informationen mit dem Dokument speichern möchten.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Verwenden Sie die CustomDocumentProperties-Eigenschaft eines Dokuments, um mit benutzerdefinierten Eigenschaften zu arbeiten. Verwenden Sie in einem Projekt auf Dokumentebene für Microsoft Office Excel z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> -Eigenschaft der `ThisWorkbook` -Klasse. Verwenden Sie in einem VSTO-Add-In-Projekt für Excel die <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> -Eigenschaft eines <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekts. Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties> -Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty> -Objekten ist. Sie können die `Item`-Eigenschaft der Auflistung verwenden, um eine bestimmte Eigenschaft nach Namen oder Index in der Auflistung abzurufen.  
  
 Das folgende Beispiel veranschaulicht, wie eine benutzerdefinierte Eigenschaft in einer Anpassung auf Dokumentebene für Excel hinzugefügt und ihr ein Wert zugewiesen wird.  
  
 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Zugriff auf und Bearbeiten von benutzerdefinierten Dokumenteigenschaften in Microsoft Word? ](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Beispiel  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Beim Versuch, auf die `Value` -Eigenschaft für nicht definierte Eigenschaften zuzugreifen, wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Vorgehensweise: Lesen aus und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)  
