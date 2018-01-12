---
title: "Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern | Microsoft Docs"
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
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 94293b90add3cbb4034278b8566ecfb1d138c09e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-worksheets"></a>Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern
  Die Schutzfunktion in Microsoft Office Excel verhindert, dass Objekte in einem Arbeitsblatt durch Benutzer und Code geändert werden. Standardmäßig werden alle Zellen gesperrt, nachdem der Schutz aktiviert wurde.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In Anpassungen auf Dokumentebene können Sie Arbeitsblätter mit dem Excel-Designer schützen. Sie können ein Arbeitsblatt in einem beliebigen Projekttyp auch zur Laufzeit programmgesteuert schützen.  
  
> [!NOTE]  
>  Geschützten Bereichen eines Arbeitsblatts können keine Windows Forms-Steuerelemente hinzugefügt werden.  
  
## <a name="using-the-designer"></a>Mithilfe des Designers  
  
#### <a name="to-protect-a-worksheet-in-the-designer"></a>So schützen Sie ein Arbeitsblatt im Designer  
  
1.  In der **Änderungen** Gruppe der **Überprüfung** auf **Blatt schützen**.  
  
     Die **Blatt schützen** Dialogfeld wird angezeigt. Sie können ein Kennwort festlegen und optional bestimmte Aktionen angeben, die Benutzer in einem Arbeitsblatt ausführen dürfen, z. B. Zellen formatieren oder Zeilen einfügen.  
  
 Sie können Benutzern auch die Bearbeitung bestimmter Bereiche in geschützten Arbeitsblättern erlauben.  
  
#### <a name="to-allow-editing-in-specific-ranges"></a>So lassen Sie die Bearbeitung bestimmter Bereiche zu  
  
1.  In der **Änderungen** Gruppe der **Überprüfung** auf **Benutzerberechtigungen zum Bearbeiten von Bereichen**.  
  
     Die **Benutzerberechtigungen zum Bearbeiten von Bereichen** Dialogfeld wird angezeigt. Sie können Bereiche angeben, die mithilfe eines Kennworts entsperrt werden, und Benutzer, die Bereiche ohne Kennwort bearbeiten können.  
  
## <a name="using-code-at-run-time"></a>Mithilfe von Code zur Laufzeit  
 Mit dem folgenden Code wird das Kennwort (unter Verwendung der getPasswordFromUser-Variablen, die ein vom Benutzer angegebenes Kennwort enthält) festgelegt und nur das Sortieren zugelassen.  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einer Anpassung auf Dokumentebene  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>-Methode des Arbeitsblatts auf. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einen VSTO-Add-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A>-Methode des aktiven Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Arbeitsblatt-Hostelements](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  