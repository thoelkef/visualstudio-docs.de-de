---
title: "Gewusst wie: Hinzuf&#252;gen von XMLMappedRange-Steuerelementen zu Arbeitsbl&#228;ttern"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "XMLMappedRange-Steuerelement, Hinzufügen zu Arbeitsblättern"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Hinzuf&#252;gen von XMLMappedRange-Steuerelementen zu Arbeitsbl&#228;ttern
  Wenn Sie einer Zelle in Microsoft Office Excel ein XML\-Element zuordnen, fügt Visual Studio dem Arbeitsblatt automatisch ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement hinzu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Das <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement ist in der **Toolbox** oder im **Datenquellenfenster** nicht verfügbar.  Zusätzlich können Sie keine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelemente programmgesteuert erstellen.  
  
### So fügen Sie einem Arbeitsblatt ein XMLMappedRange\-Steuerelement hinzu  
  
1.  Öffnen Sie die Excel\-Arbeitsmappe im Visual Studio\-Designer.  
  
2.  Öffnen Sie das Arbeitsblatt, dem das Steuerelement hinzugefügt werden soll.  
  
3.  Klicken Sie auf der Registerkarte **Entwickler** auf **Quelle**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** auf dem Menüband nicht sichtbar ist, müssen Sie diese zuerst aktivieren.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Der Aufgabenbereich **XML\-Quelle** wird angezeigt.  
  
4.  Klicken Sie im Aufgabenbereich **XML\-Quelle** auf **XML\-Zuordnungen**.  
  
5.  Klicken Sie im Dialogfeld **XML\-Zuordnungen** auf die Schaltfläche **Hinzufügen**.  
  
     Das Dialogfeld **XML\-Quelle** wird angezeigt.  
  
6.  Wählen Sie im Dialogfeld **XML\-Quelle** ein XML\-Schema aus, und klicken Sie auf **Öffnen**.  
  
     Dem Dialogfeld **XML\-Zuordnungen** wird das Schema hinzugefügt.  
  
7.  Klicken Sie im Dialogfeld **XML\-Zuordnungen** auf **OK**.  
  
8.  Ziehen Sie ein Element vom Aufgabenbereich **XML\-Quelle** in eine Zelle auf dem Arbeitsblatt.  
  
     Es wird ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> erstellt und dem Projekt hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie ein übergeordnetes Element aus dem Aufgabenbereich **XML\-Quelle** ziehen, wird ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement erstellt.  
  
## Siehe auch  
 [XmlMappedRange-Steuerelement](../vsto/xmlmappedrange-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  