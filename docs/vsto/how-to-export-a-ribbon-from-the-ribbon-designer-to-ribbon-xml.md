---
title: "Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML"
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
  - "Benutzerdefiniertes Menüband, XML"
  - "Anpassen des Menübands, XML"
  - "Exportieren der Multifunktionsleiste"
  - "Menüband [Office-Entwicklung in Visual Studio], Exportieren"
  - "Menüband [Office-Entwicklung in Visual Studio], XML"
  - "Menüband-Designer [Office-Entwicklung in Visual Studio]"
  - "XML [Office-Entwicklung in Visual Studio], Menüband"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML
  Das Element **Menüband \(Visual Designer\)** unterstützt nicht alle möglichen Typen der Menübandanpassung.  Wenn Sie erweiterte Anpassungsoptionen für das Menüband nutzen möchten, können Sie das Menüband vom Designer nach Menüband\-XML exportieren und das XML direkt bearbeiten.  
  
> [!NOTE]  
>  In der Menüband\-XML\-Datei werden nicht alle Eigenschaftswerte angezeigt.  Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### So exportieren Sie ein Menüband vom Menüband\-Designer nach Menüband\-XML:  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Menüband\-Codedatei, und klicken Sie danach auf **Ansicht\-Designer**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Menüband\-Designer, und klicken Sie anschließend auf **Menüband nach XML exportieren**.  
  
     Visual Studio fügt dem Projekt eine Menüband\-XML\-Datei und eine Menüband\-XML\-Codedatei hinzu.  
  
3.  Suchen Sie in der Menüband\-Codeklasse die Kommentare, die mit `TODO:.` beginnen.  
  
4.  Kopieren Sie den Codeblock in diesen Kommentaren in die Klasse **ThisAddin**, **ThisWorkbook** oder **ThisDocument**, und zwar abhängig davon, welchen Projektmappentyp Sie entwickeln.  
  
     Mit diesem Code kann die Microsoft Office\-Anwendung das benutzerdefinierte Menüband erkennen und laden.  Weitere Informationen finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
5.  Nehmen Sie in der Klasse **ThisAddin**, **ThisWorkbook** oder **ThisDocument** eine Auskommentierung des Codeblocks vor.  
  
     Nachdem Sie die Auskommentierung des Codes aufgehoben haben, sollte der Code etwa wie folgt aussehen.  In diesem Beispiel wird die Menübandklasse als `MyRibbon` bezeichnet.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Wechseln Sie zur Menüband\-XML\-Codedatei, und suchen Sie den Bereich `Ribbon Callbacks`.  
  
     Dort werden Rückrufmethoden zum Behandeln von Benutzeraktionen geschrieben \(beispielsweise Klicken auf eine Schaltfläche\).  
  
7.  Erstellen Sie eine Rückrufmethode für jeden Ereignishandler, den Sie im Menüband\-Designercode geschrieben haben.  
  
8.  Verschieben Sie den gesamten Ereignishandlercode von den Ereignishandlern zu den Rückrufmethoden, und ändern Sie den Code so, dass er mit dem Programmiermodell für die Erweiterbarkeit von Menübändern \(RibbonX\) kompatibel ist.  
  
     Weitere Informationen zum Schreiben von Rückrufmethoden und zum Verwenden des RibbonX\-Programmiermodells finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  