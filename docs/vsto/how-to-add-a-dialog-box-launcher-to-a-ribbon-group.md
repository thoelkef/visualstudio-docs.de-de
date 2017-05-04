---
title: "Gewusst wie: Hinzuf&#252;gen eines Dialogfeld-Startprogramms zu einer Multifunktionsleistengruppe | Microsoft Docs"
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
  - "Dialogfeld-Startprogramm [Office-Entwicklung in Visual Studio]"
  - "Menüband [Office-Entwicklung in Visual Studio], Dialogfeld-Startprogramm"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Hinzuf&#252;gen eines Dialogfeld-Startprogramms zu einer Multifunktionsleistengruppe
  Ein Dialogfeldstartprogramm kann jeder beliebigen Gruppe auf einem Menüband hinzugefügt werden.  Ein Dialogfeldstartprogramm ist ein kleines Symbol, das in einer Gruppe angezeigt wird.  Benutzer klicken auf dieses Symbol, um verwandte Dialogfelder oder Aufgabenbereiche zu öffnen, die zusätzliche gruppenbezogene Optionen beinhalten.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### So fügen Sie einer Menübandgruppe ein Dialogfeldstartprogramm hinzu  
  
1.  Wählen Sie die Codedatei für das Menüband \(VB\- oder CS\-Datei\) im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Designer**.  
  
3.  Klicken Sie im Menüband\-Designer mit der rechten Maustaste auf eine beliebige Gruppe, und klicken Sie anschließend auf **DialogBoxLauncher hinzufügen**.  
  
     Fügen Sie dem <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>\-Ereignis der Gruppe Code hinzu, um ein benutzerdefiniertes oder integriertes Dialogfeld zu öffnen.  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  