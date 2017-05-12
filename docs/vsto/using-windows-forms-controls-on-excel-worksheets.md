---
title: "Verwenden von Windows&#160;Forms-Steuerelementen in Excel-Arbeitsbl&#228;ttern"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Excel [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Verwenden von Windows&#160;Forms-Steuerelementen in Excel-Arbeitsbl&#228;ttern
  Das Hinzufügen von Windows Forms\-Steuerelementen zu Microsoft Office Excel\-Arbeitsmappen erfolgt auf die gleiche Weise wie das Hinzufügen von Steuerelementen zu Windows Forms.  Allgemeine Informationen zum Arbeiten mit Steuerelementen in Dokumenten finden Sie unter [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Überlegungen zur Verwendung von Steuerelementen für Excel  
 Es gibt einige Aspekte zu beachten, die für Excel spezifisch sind.  
  
### Abgleichen der Steuerelementgröße mit der Zellgröße  
 Sie können das Steuerelement so konfigurieren, dass dessen Größe automatisch bei Änderung der Größe der übergeordneten Zelle geändert wird.  Weitere Informationen finden Sie unter [Gewusst wie: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Hinzufügen von Komponenten, die von allen Arbeitsmappen freigegeben werden  
 Sie können Komponenten, die Sie für alle Arbeitsblätter freigeben möchten \(z.&nbsp;B. <xref:System.Data.DataSet>\), dem Arbeitsmappen\-Designer anstelle den Arbeitsmappen hinzufügen.  Die Komponente wird auf der Komponentenleiste angezeigt.  
  
### Formel für das Einbetten von Steuerelementen  
 Wenn Sie in Excel ein Steuerelement auswählen, wird in der **Bearbeitungsleiste\=EMBED\("WinForms.Control.Host",""\)** angezeigt.  Dieser Text ist notwendig und sollte nicht gelöscht werden.  
  
## Siehe auch  
 [Gewusst wie: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  