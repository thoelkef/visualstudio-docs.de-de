---
title: "Gewusst wie: Hinzuf&#252;gen von Steuerelementen zur Backstage-Ansicht"
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
  - "Steuerelemente, Menüband"
  - "Benutzerdefiniertes Menüband, Menüs"
  - "Anpassen des Menübands, Menüs"
  - "Menüs, Anpassen"
  - "Microsoft Office-Schaltfläche"
  - "Microsoft Office-Menü"
  - "Office-Schaltfläche"
  - "Menüband, Anpassen"
  - "Menüband, Menüs"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Hinzuf&#252;gen von Steuerelementen zur Backstage-Ansicht
  Sie können den Menüband\-Designer verwenden, um Menü Steuerelemente hinzuzufügen, das geöffnet wird, wenn Sie auf die Registerkarte **Datei** klicken.  Wenn Sie die Anwendung ausführen, werden Steuerelemente, die Sie **Datei** die Registerkarte hinzufügen, eine Gruppe, die **Add\-Ins** genannt wird.  
  
 Sie können keine Steuerelemente vor oder nach integrierten Steuerelementen, mit dem Menüband\-Designer in Visual Studio.  Bei einem integrierten Steuerelement ist ein Steuerelement, das bereits in der Backstage\-Ansicht angezeigt wird.  Wenn Sie Steuerelemente vor oder nach integrierten Steuerelementen positionieren möchten, müssen Sie ein Menüband\-XML verwenden.  Weitere Informationen zu **Menüband \(XML\)**, finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  Weitere Informationen zum Anpassen der Backstage\-Ansicht finden Sie unter [Introduction to the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189) und [Customizing the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### So fügen Sie Steuerelemente Backstage\-Ansicht hinzufügen  
  
1.  Öffnen Sie das Menübandelement in der Entwurfsansicht.  
  
     Weitere Informationen zum Hinzufügen eines Elements von **Menüband \(Visual Designer\)** zum Projekt finden Sie unter [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Klicken Sie im Menüband\-Designer auf die Registerkarte **Datei**.  
  
     Ein Menü\-Designer wird angezeigt.  Diese Entwurfsoberfläche beinhaltet keine Steuerelemente.  
  
3.  Ziehen Sie von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** ein beliebiges der folgenden Steuerelemente zum Menü\-Designer:  
  
    -   Button  
  
    -   CheckBox  
  
    -   Katalog  
  
    -   Menü  
  
    -   Trennzeichen  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Ziehen Sie Steuerelemente, um Sie an neue Positionen im Menü zu verschieben.  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  