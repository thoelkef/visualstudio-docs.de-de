---
title: 'Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e240f4b4be5ce4092705615f060f4e0ef0076e3a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254474"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken
  Wenn Sie ein Microsoft Office Excel-Dokument, die Windows Forms-Steuerelemente enthält drucken, sind die Steuerelemente auf dem Arbeitsblatt gedruckter sichtbar. Sie können die Steuerelemente ausblenden beim Drucken eines Arbeitsblatts.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Wenn Sie Steuerelemente ausblenden, die Daten, wie z. B. angezeigt eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, die Daten in das Steuerelement nicht im Arbeitsblatt gedruckter angezeigt werden.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Zum Ausblenden von Steuerelementen, wenn ein Arbeitsblatt gedruckter  
  
1.  Erstellen oder öffnen Sie ein Excel-Projekt in Visual Studio, und überprüfen Sie, ob **Sheet1** im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Aus der **Standardsteuerelementen** Registerkarte der **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.Button> die Steuerung an eine Zelle auf `Sheet1`.  
  
3.  In der **Eigenschaften** legen die <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> Eigenschaft **"false"**.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Gewusst wie: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  