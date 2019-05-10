---
title: 'Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d6fb66684bd51c75e655bc2403cb6a9fb5846a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438817"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern
  Die Schutzfunktion in Microsoft Office Excel verhindert, dass Objekte in einem Arbeitsblatt durch Benutzer und Code geändert werden. Standardmäßig werden alle Zellen gesperrt, nachdem der Schutz aktiviert wurde.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In Anpassungen auf Dokumentebene können Sie Arbeitsblätter mit dem Excel-Designer schützen. Sie können ein Arbeitsblatt in einem beliebigen Projekttyp auch zur Laufzeit programmgesteuert schützen.

> [!NOTE]
> Geschützten Bereichen eines Arbeitsblatts können keine Windows Forms-Steuerelemente hinzugefügt werden.

## <a name="use-the-designer"></a>Mithilfe des Designers

### <a name="to-protect-a-worksheet-in-the-designer"></a>So schützen Sie ein Arbeitsblatt im Designer

1. In der **Änderungen** Gruppe der **Review** auf **Blatt schützen**.

    Die **Blatt schützen** Dialogfeld wird angezeigt. Sie können ein Kennwort festlegen und optional bestimmte Aktionen angeben, die Benutzer in einem Arbeitsblatt ausführen dürfen, z. B. Zellen formatieren oder Zeilen einfügen.

   Sie können Benutzern auch die Bearbeitung bestimmter Bereiche in geschützten Arbeitsblättern erlauben.

### <a name="to-allow-editing-in-specific-ranges"></a>So lassen Sie die Bearbeitung bestimmter Bereiche zu

1. In der **Änderungen** Gruppe der **Review** auf **Benutzerberechtigungen zum Bearbeiten von Bereichen**.

     Die **Benutzerberechtigungen zum Bearbeiten von Bereichen** Dialogfeld wird angezeigt. Sie können Bereiche angeben, die mithilfe eines Kennworts entsperrt werden, und Benutzer, die Bereiche ohne Kennwort bearbeiten können.

## <a name="use-code-at-runtime"></a>Verwenden von Code zur Laufzeit
 Mit dem folgenden Code wird das Kennwort (unter Verwendung der getPasswordFromUser-Variablen, die ein vom Benutzer angegebenes Kennwort enthält) festgelegt und nur das Sortieren zugelassen.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einer Anpassung auf Dokumentebene

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> -Methode des Arbeitsblatts auf. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1`arbeiten.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>So schützen Sie ein Arbeitsblatt mithilfe von Code in einen VSTO-Add-In

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> -Methode des aktiven Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)
- [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
