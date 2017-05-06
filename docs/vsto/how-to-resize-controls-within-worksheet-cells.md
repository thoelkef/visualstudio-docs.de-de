---
title: "Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Steuerelementen innerhalb der Arbeitsblattzellen"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Größenänderung"
  - "Verwaltete Steuerelemente, Größenänderung"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Größenänderung"
  - "Arbeitsblätter, Größenänderung"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Steuerelementen innerhalb der Arbeitsblattzellen
  Wenn Sie die Spalten\- oder Zeilengröße in einem Arbeitsblatt ändern, werden alle darin enthaltenen Hoststeuerelemente automatisch der Höhe oder Breite der geänderten Zelle angepasst.  Windows Forms\-Steuerelemente führen standardmäßig keine Größenänderung durch.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Wenn Sie die Steuerelemente zur Entwurfszeit hinzufügen, müssen Sie Positionierungsoptionen für jedes Steuerelement festlegen.  
  
 Falls Sie ein Windows Forms\-Steuerelement programmgesteuert hinzufügen und ein Bereichsargument angeben, ändert das Steuerelement automatisch seine Größe, wenn die Größe einer Zelle innerhalb des Bereichs geändert wird.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Ändern der Größe von Steuerelementen zur Entwurfszeit  
  
#### So ändern Sie gleichzeitig die Größe von Steuerelementen und Zellen zur Entwurfszeit  
  
1.  Ziehen Sie aus der **Toolbox** ein Windows Forms\-Steuerelement auf ein Arbeitsblatt.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Steuerelement, und klicken Sie dann auf **Steuerelement formatieren**.  
  
3.  Klicken Sie im Menü **Steuerelement formatieren** auf die Registerkarte **Eigenschaften**.  
  
4.  Wählen Sie unter **Objektpositionierung** die Option **Von Zellposition und \-größe abhängig** aus, und klicken Sie dann auf **OK**.  
  
     Wenn Sie die Größe der Zelle mit dem Steuerelement ändern, passt sich das Steuerelement der Zellengröße an.  
  
## Ändern der Größe von Steuerelementen zur Laufzeit  
 Wenn Sie ein Windows Forms\-Steuerelement zur Laufzeit hinzufügen und einen <xref:Microsoft.Office.Interop.Excel.Range> als Position des Steuerelements übergeben, wird das Steuerelement automatisch seine Größe ändern, sobald die Arbeitsblattzelle, die den Bereich enthält, in der Größe geändert wird.  
  
#### So lassen Sie die Größe von Steuerelementen und Zellen zur Laufzeit gemeinsam ändern  
  
1.  Fügen Sie ein Steuerelement zum Bereich A1 hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     Wenn Sie die Größe der Zelle mit dem Steuerelement ändern, passt sich das Steuerelement der Zellengröße an.  
  
## Zurücksetzen der Steuerelementplatzierung  
 Sie können die Platzierung und Größenänderung des Steuerelements zurücksetzen, indem Sie für die `Placement`\-Eigenschaft einen der folgenden <xref:Microsoft.Office.Interop.Excel.XlPlacement>\-Werte festlegen:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### So ändern Sie das Verhalten eines Steuerelements, damit es nicht zusammen mit der Zelle die Größe ändert oder sich verschiebt  
  
1.  Rufen Sie die Platzierungseigenschaft des Steuerelements auf, und legen Sie den Wert auf <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  