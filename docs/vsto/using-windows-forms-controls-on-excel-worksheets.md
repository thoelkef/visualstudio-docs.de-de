---
title: "Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern | Microsoft Docs"
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
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bbd9c19698a9c81b5af29d27bba91b8aa36dcd2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Verwenden von Windows Forms-Steuerelementen in Excel-Arbeitsblättern
  Sie können Windows Forms-Steuerelemente Ihre Microsoft Office Excel-Arbeitsmappen auf die gleiche Weise hinzufügen, dass Sie in Windows Forms-Steuerelemente hinzufügen. Allgemeine Informationen zum Arbeiten mit Steuerelementen in Dokumenten finden Sie unter [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Steuerelement-Überlegungen für Excel  
 Es gibt einige Überlegungen, die für Excel spezifisch sind.  
  
### <a name="matching-control-size-to-cell-size"></a>Abgleichen der Steuerelementgröße mit der Zellgröße  
 Sie können ein Steuerelement so konfigurieren, dass dessen Größe automatisch bei Änderung der Größe der übergeordneten Zelle geändert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Steuerelemente in Zellen im Arbeitsblatt Größe](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Hinzufügen von Komponenten, die auf allen Arbeitsblättern nutzbar sein sollen  
 Sie können Komponenten, die auf allen Arbeitsblättern nutzbar sein sollen (etwa ein <xref:System.Data.DataSet>), dem Arbeitsmappen-Designer hinzufügen, statt sie den Arbeitsblättern hinzuzufügen. Die Komponente wird auf der Komponentenleiste angezeigt.  
  
### <a name="formula-for-embedding-controls"></a>Formel für das Einbetten von Steuerelementen  
 Wenn Sie in Excel ein Steuerelement auswählen, wird **=EMBED("WinForms.Control.Host","")** in der **Formelleiste**angezeigt. Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  