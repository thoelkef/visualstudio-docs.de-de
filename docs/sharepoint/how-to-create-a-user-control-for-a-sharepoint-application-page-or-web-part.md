---
title: "Gewusst wie: Erstellen eines Benutzersteuerelements f&#252;r eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Benutzersteuerelemente [SharePoint-Entwicklung in Visual Studio], Hinzufügen"
  - "Benutzersteuerelemente [SharePoint-Entwicklung in Visual Studio], Erstellen"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Erstellen eines Benutzersteuerelements f&#252;r eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart
  Sie können benutzerdefinierte Benutzersteuerelemente erstellen, die benutzerdefinierte Funktionalität für die SharePoint\-Lösung bereitstellen, und Sie können diese Funktion im Projekt wiederverwenden.  Sie können die Benutzersteuerelemente in einem Webpart oder einer Anwendungsseite verwenden, weitere ASP.NET\- und SharePoint\-Steuerelemente hinzufügen und Eigenschaften sowie Methoden für das Steuerelement definieren.  Weitere Informationen zu Benutzersteuerelementen finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) und in folgendem Blogbeitrag zu [Benutzersteuerelementen und Serversteuerelementen in SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### So erstellen Sie ein Benutzersteuerelement für SharePoint  
  
1.  Öffnen oder erstellen Sie in Visual Studio ein SharePoint\-Projekt.  
  
     Siehe [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten aus.  
  
3.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
4.  Wählen Sie im Bereich **Installiert** den Knoten **Office\/SharePoint** aus.  
  
5.  Wählen Sie in der Liste der SharePoint\-Vorlagen **Benutzersteuerelement \(nur Farmlösung\)** aus.  
  
    > [!NOTE]  
    >  Benutzersteuerelemente funktionieren nur in Farmlösungen.  
  
6.  Geben Sie im Feld **Name** einen Namen für das Benutzersteuerelement an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu.  Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Standardmäßig wird die Benutzersteuerelementdatei in der Ansicht **Quelle** des Visual Web Developer\-Designers angezeigt.  In dieser Ansicht können Sie das XML\-Markup des Steuerelements bearbeiten.  Sie können zur Ansicht **Entwurf** wechseln, wenn Sie das Steuerelement durch Ziehen von Steuerelementen von der **Toolbox** visuell entwerfen möchten.  Siehe [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/de-de/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Wenn Sie Ereignisse behandeln, die im Steuerelement auftreten, fügen Sie der Codedatei des Benutzersteuerelements Code hinzu.  
  
     Diese Datei wird im **Projektmappen\-Explorer** unter der Benutzersteuerelementdatei angezeigt und hat in Abhängigkeit von der Sprache des Projekts eine CS\- oder VB\-Dateinamenerweiterung.  
  
## Siehe auch  
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  