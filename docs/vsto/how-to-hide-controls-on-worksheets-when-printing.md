---
title: "Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsbl&#228;ttern beim Drucken | Microsoft Docs"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Ausblenden beim Drucken"
  - "Drucken [Office-Entwicklung in Visual Studio], Ausblenden von Steuerelementen"
  - "Drucken [Office-Entwicklung in Visual Studio], Arbeitsblätter"
  - "Arbeitsblätter, Ausblenden von Steuerelementen beim Drucken"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsbl&#228;ttern beim Drucken
  Beim Drucken eines Microsoft Office Excel\-Dokuments mit Windows Forms\-Steuerelementen sind die Steuerelemente auf dem ausgedruckten Arbeitsblatt sichtbar.  Sie können die Steuerelemente beim Drucken eines Arbeitsblatts ausblenden.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Wenn Sie Steuerelemente ausblenden, die Daten anzeigen \(z. B. <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>\), sind die im Steuerelement enthaltenen Daten auf dem gedruckten Arbeitsblatt nicht sichtbar.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So blenden Sie Steuerelemente für das Drucken eines Arbeitsblatts aus  
  
1.  Erstellen oder öffnen Sie ein Excel\-Projekt in Visual Studio, und stellen Sie sicher, dass im Designer **Sheet1** angezeigt wird.  Informationen zum Erstellen von Projekten finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>\-Steuerelement in eine Zelle von `Sheet1`.  
  
3.  Legen Sie im **Eigenschaftenfenster** die <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A>\-Eigenschaft auf **False** fest.  
  
## Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Gewusst wie: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  