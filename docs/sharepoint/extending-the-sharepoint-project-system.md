---
title: "Extending the SharePoint Project System | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  Sie können SharePoint\-Lösungen erstellen, indem Sie einen Satz von Projekt\- und Elementvorlagen in Visual Studio.  Diese Vorlagen erfüllen die Anforderungen vieler Entwicklungsszenarien, aber Sie können möglicherweise mehrere Fälle, in denen sie nicht Funktionalität, die Sie benötigen.  In diesen Fällen können Sie das SharePoint\-Projektsystem erweitern.  
  
## Übersicht über das SharePoint\-Projektsystem  
 Die grundlegende Komponente des SharePoint\-Projektsystems sind *SharePoint\-Projektelemente*.  Ein SharePoint\-Projektelement stellt eine SharePoint\-Anpassung dar, z. B. eine Listendefinition, ein Webpart oder einen Inhaltstyp.  
  
 Ein SharePoint\-Projekt ist ein Visual Studio\-Projekt, das ein oder mehrere SharePoint\-Projektelemente enthält.  SharePoint\-Projekte enthalten auch zusätzliche Komponenten, die definieren, wie Projektelemente für die Bereitstellung in Funktionen und Paketen gruppiert werden.  
  
 Weitere Informationen zum Inhalt der SharePoint\-Projektelemente und SharePoint\-Projekte finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Erweitern des SharePoint\-Projektsystems  
 Sie können das SharePoint\-Projektsystem auf die folgende Weise erweitern:  
  
-   Definieren Sie eigene SharePoint\-Projektelementtypen, und ordnen Sie sie neuen Elementvorlagen oder Projektvorlagen in Visual Studio zu.  Sie können z. B. einen SharePoint\-Projektelementtyp definieren, um eine benutzerdefinierte Aktion oder ein Felds zu erstellen.  Weitere Informationen finden Sie unter [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Erweitern Sie SharePoint\-Projektelementtypen, die bereits in Visual Studio installiert sind.  Beispielsweise können Sie ein Kontextmenüelement einem Projektelement in **Projektmappen\-Explorer** hinzufügen und das Projektelement anpassen, wenn ein Entwickler auf das Menüelement auswählt.  Weitere Informationen finden Sie unter [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Erweitern Sie SharePoint\-Projekte.  Sie können z. B. Ereignishandler hinzufügen, um bestimmte Aufgaben auszuführen, wenn Elemente hinzugefügt oder aus SharePoint\-Projekten entfernt werden.  Weitere Informationen finden Sie unter [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md).  
  
-   Erweitern Sie das Verpackungs\- und Bereitstellungsverhalten von SharePoint\-Projektelementen und SharePoint\-Projekten.  Sie können z. B. eigene Bereitstellungsschritte erstellen, die beim Bereitstellen oder Zurücknehmen eines Projekts ausgeführt werden, oder Sie können zusätzliche benutzerdefinierte Aufgaben ausführen, wenn Visual Studio bestimmte Bereitstellungsschritte ausführt.  Weitere Informationen finden Sie unter [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## Allgemeine Entwicklungsaufgaben  
 Sie können folgende gängigen Aufgaben in Erweiterungen des SharePoint\-Projektsystems ausführen:  
  
-   Speichern Sie benutzerdefinierte Zeichenfolgendaten mit Projektelementen und in verschiedenen Typen von Projektdateien.  Weitere Informationen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Konvertieren eines Objekts im SharePoint\-Projektsystem in einem entsprechenden Objekt im Visual Studio\-Automatisierungsobjektmodell oder \-Integrationsobjektmodell und umgekehrt.  Weitere Informationen finden Sie unter [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## Siehe auch  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  