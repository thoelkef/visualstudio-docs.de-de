---
title: Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 144bcf1d9b0b96944e1493471106fe8aa6c8031b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871532"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern
  Sie können Windows Forms-Steuerelementen zu Ihren Microsoft Office Excel-Arbeitsmappen auf die gleiche Weise hinzufügen, Windows Forms Steuerelemente hinzuzufügen. Allgemeine Informationen zum Arbeiten mit Steuerelementen in Dokumenten finden Sie unter [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Steuerelement-Überlegungen für Excel  
 Es gibt einige Überlegungen, die für Excel spezifisch sind.  
  
### <a name="match-control-size-to-cell-size"></a>Anpassen der Größe des Steuerelements Größe der Zelle  
 Sie können ein Steuerelement so konfigurieren, dass dessen Größe automatisch bei Änderung der Größe der übergeordneten Zelle geändert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Hinzufügen von Komponenten, die von allen Arbeitsblättern gemeinsam genutzt werden  
 Sie können Komponenten, die auf allen Arbeitsblättern nutzbar sein sollen (etwa ein <xref:System.Data.DataSet>), dem Arbeitsmappen-Designer hinzufügen, statt sie den Arbeitsblättern hinzuzufügen. Die Komponente wird auf der Komponentenleiste angezeigt.  
  
### <a name="formula-for-embedding-controls"></a>Formel für ein Einbetten der Steuerelemente  
 Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Exemplarische Vorgehensweise: Ändern der arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
