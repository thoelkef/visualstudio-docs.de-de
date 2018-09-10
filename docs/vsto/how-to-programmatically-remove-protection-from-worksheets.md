---
title: 'Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e15fd2f2d4a025155bbaa1d39dc5c38155b452e2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673472"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern
  Sie können den Schutz programmgesteuert aus einem Microsoft Office Excel-Arbeitsblatt entfernen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgenden Beispiel wird die Variable `getPasswordFromUser`befindet, die ein vom Benutzer erhaltenes Kennwort enthält.  
  
## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>So heben Sie den Schutz eines Arbeitsblatts bei der Anpassung auf Dokumentebene auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> Methode des Arbeitsblatts, und übergeben Sie das Kennwort bei Bedarf. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Zum Aufheben des Schutzes von einem Arbeitsblatt in einem VSTO-Add-in  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> Methode des aktiven Arbeitsblatts, und übergeben Sie das Kennwort bei Bedarf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  