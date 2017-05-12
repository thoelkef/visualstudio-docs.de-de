---
title: "Gewusst wie: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt"
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
  - "Spalten [Office-Entwicklung in Visual Studio], Aufheben von Gruppierungen"
  - "Gruppen"
  - "Gruppen [Office-Entwicklung in Visual Studio], Löschen in Arbeitsblättern"
  - "Gruppen, Erstellen in Arbeitsblättern"
  - "Bereiche, Erstellen von Gruppen"
  - "Zeilen [Office-Entwicklung in Visual Studio], Aufheben von Gruppierungen"
  - "Arbeitsblätter, Löschen von Gruppen"
  - "Arbeitsblätter, Erstellen von Gruppen"
  - "Arbeitsblätter, Aufheben der Gruppierung von Zeilen und Spalten"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt
  Sie können eine oder mehrere ganze Zeilen gruppieren.  Wenn Sie eine Gruppe in einem Arbeitsblatt erstellen möchten, verwenden Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement oder ein systemeigenes Excel\-Bereichsobjekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden eines NamedRange\-Steuerelements  
 Wenn Sie einem Projekt auf Dokumentebene zur Entwurfszeit ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzufügen, können Sie mithilfe des Steuerelements programmgesteuert eine Gruppe erstellen.  Das folgende Beispiel geht von drei <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelementen im selben Arbeitsblatt aus: `data2001`, `data2002` und `dataAll`.  Jeder benannte Bereich verweist auf eine ganze Zeile im Arbeitsblatt.  
  
#### So erstellen Sie eine Gruppe von NamedRange\-Steuerelementen in einem Arbeitsblatt  
  
1.  Gruppieren Sie drei benannte Bereiche, indem Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A>\-Methode der einzelnen Bereiche aufrufen.  Dieser Code muss in eine Sheet\-Klasse, nicht in die `ThisWorkbook`\-Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>\-Methode auf, um die Gruppierung von Zeilen aufzuheben.  
  
## Verwenden von systemeigenen Excel\-Bereichen  
 Der folgende Code geht von drei Excel\-Bereichen mit dem Namen `data2001`, `data2002` und `dataAll` in einem Arbeitsblatt aus.  
  
#### So erstellen Sie eine Gruppe von Excel\-Bereichen in einem Arbeitsblatt  
  
1.  Gruppieren Sie drei benannte Bereiche, indem Sie die <xref:Microsoft.Office.Interop.Excel.Range.Group%2A>\-Methode der einzelnen Bereiche aufrufen.  Das folgende Beispiel geht von drei <xref:Microsoft.Office.Interop.Excel.Range>\-Steuerelementen mit dem Namen `data2001`, `data2002` und `dataAll` im selben Arbeitsblatt aus.  Jeder benannte Bereich verweist auf eine ganze Zeile im Arbeitsblatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>\-Methode auf, um die Gruppierung von Zeilen aufzuheben.  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  