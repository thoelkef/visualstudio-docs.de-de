---
title: "Vorgehensweise: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern | Microsoft Docs"
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
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b4564baab3cf2daa6e8859a66dbc6e9e06ffdef
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern
  Sie können den Schutz programmgesteuert aus einem Microsoft Office Excel-Arbeitsblatt entfernen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgenden Beispiel wird die Variable `getPasswordFromUser`befindet, die ein vom Benutzer erhaltenes Kennwort enthält.  
  
### <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>So heben Sie den Schutz eines Arbeitsblatts bei der Anpassung auf Dokumentebene auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> -Methode des Arbeitsblatts auf, und übergeben Sie bei Bedarf das Kennwort. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
### <a name="to-unprotect-a-worksheet-in-an-vsto-add-in"></a>So heben Sie den Schutz für ein Arbeitsblatt in einem VSTO-Add-In auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> -Methode des aktiven Arbeitsblatts auf, und übergeben Sie bei Bedarf das Kennwort.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  