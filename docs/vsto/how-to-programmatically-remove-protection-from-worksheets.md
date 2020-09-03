---
title: 'Vorgehensweise: Programm gesteuertes Entfernen des Schutzes von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519872"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Vorgehensweise: Programm gesteuertes Entfernen des Schutzes von Arbeitsblättern
  Sie können den Schutz programmgesteuert aus einem Microsoft Office Excel-Arbeitsblatt entfernen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Im folgenden Beispiel wird die Variable `getPasswordFromUser`befindet, die ein vom Benutzer erhaltenes Kennwort enthält.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>So heben Sie den Schutz eines Arbeitsblatts bei der Anpassung auf Dokumentebene auf

1. Wenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> -Methode des Arbeitsblatts an, und übergeben Sie ggf. das Kennwort. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>So heben Sie den Schutz für ein Arbeitsblatt in einem VSTO-Add-in auf

1. Wenden Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> -Methode des aktiven Arbeitsblatts an, und übergeben Sie ggf. das Kennwort.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
