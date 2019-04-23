---
title: 'Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a236b30552007112663ad9f985ddc94995fe1ef8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050023"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken
  Wenn Sie ein Microsoft Office Excel-Dokument, die Windows Forms-Steuerelemente enthält drucken, sind die Steuerelemente auf dem Arbeitsblatt gedruckter sichtbar. Sie können die Steuerelemente ausblenden beim Drucken eines Arbeitsblatts.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
>  Wenn Sie Steuerelemente ausblenden, die Daten, wie z. B. angezeigt eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, die Daten in das Steuerelement nicht im Arbeitsblatt gedruckter angezeigt werden.

> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Zum Ausblenden von Steuerelementen, wenn ein Arbeitsblatt gedruckter

1. Erstellen oder öffnen Sie ein Excel-Projekt in Visual Studio, und überprüfen Sie, ob **Sheet1** im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Aus der **Standardsteuerelementen** Registerkarte der **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.Button> die Steuerung an eine Zelle auf `Sheet1`.

3. In der **Eigenschaften** legen die <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> Eigenschaft **"false"**.

## <a name="see-also"></a>Siehe auch
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)
