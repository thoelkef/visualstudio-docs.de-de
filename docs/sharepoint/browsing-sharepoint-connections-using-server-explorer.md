---
title: "Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Verbindungen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Durchsuchen von SharePoint-Websites"
  - "SharePoint-Entwicklung in Visual Studio, SharePoint-Verbindungen"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer
  Sie können lokale SharePoint\-Verbindungen jetzt im **Server\-Explorer** durchsuchen.  Auf diese Weise verwenden, können Sie durch die Komponenten einer SharePoint\-Website auf dem System navigieren.  SharePoint\-Websitekomponenten, wie Listendefinitionen und Inhaltstypen, werden in einem Knoten der **SharePoint\-Verbindungen**, in der Strukturansicht des **Server\-Explorer**.  Um **Server\-Explorer**, auf der Menüleiste anzuzeigen, wählen Sie **Server\-Explorer**, **Ansicht** aus.  die SharePoint\-Websitekomponenten anzeigen, können Sie Elemente entfernen, ihrer Eigenschaften sowie das Aktualisieren, indem Sie Befehle im Kontextmenü verwenden.  
  
> [!IMPORTANT]  
>  Zum Durchsuchen einer SharePoint\-Website, müssen Sie Administrator die SharePoint\-Websitesammlung sein, und Visual Studio als Administrator des lokalen Computers ausführen.  Andernfalls wird die Website im **Server\-Explorer**, die Knoten können aber nicht erweitern.  Um sicherzustellen dass Sie Administrator der Websiteauflistung sind, die Website in einem Webbrowser öffnen, das Menü **Websiteaktionen** öffnen, und dann, auf der Seite **Berechtigungen: TeamwebsiteWebsiteberechtigungen** auswählen, wählen Sie den Befehl **Websitesammlungsadministratoren** aus der Gruppe **Verwalten** auf dem Menüband.  Ihr Name wird im Textfeld angezeigt, wenn Sie Websiteauflistungsadministrator sind.  Wenn der Befehl **Websitesammlungsadministratoren** nicht in der verwaltensgruppe auf dem Menüband angezeigt wird, sind Sie nicht Administrator für die Siteauflistung, und Sie müssen die entsprechenden Berechtigungen der Websiteadministrator abrufen.  
  
## Knoten des Server\-Explorers  
 Jede Komponente einer SharePoint\-Website wird durch einen Knoten in der Strukturansicht **Server\-Explorer** unter **SharePoint\-Verbindungen** dargestellt.  SharePoint\-Standardwebsites schließen beispielsweise einen Inhaltstyp namens Diskussion ein, der einen Diskussionstyp darstellt, der auf der Seite **Diskussionen** der SharePoint\-Website angezeigt wird.  Der Inhaltstyp Diskussion enthält mehrere Felder.  Um diese Felder im **Server\-Explorer** anzuzeigen, erweitern Sie den Knoten **Inhaltstypen** und dann den Knoten **Diskussion**.  Darunter befinden sich mehrere Feldknoten, z. B. Text, Diskussionsbetreff und Titel.  
  
## Kontextmenübefehle der Knoten  
 Jeder Knoten verfügt über ein Kontextmenü, auf das Sie zugreifen, indem Sie mit der rechten Maustaste auf den Knoten klicken oder ihn auswählen und dann die UMSCHALT\+F10\-TASTEN auswählen.  Knotenbefehle können Folgendes einschließen:  
  
|Befehlsname|**Beschreibung**|  
|-----------------|----------------------|  
|Aktualisieren|Aktualisiert die Strukturansicht, um die Änderungen wiederzugeben, die möglicherweise seit dem letzten Anzeigen des Knotens vorgenommen wurde.|  
|Löschen|Entfernt den ausgewählten Knoten aus der Strukturansicht. **Note:**  Dieser Befehl ist nur für SharePoint\-Verbindungen aktiviert, die unter dem Knoten **SharePoint\-Verbindungen** aufgeführt sind.|  
|Eigenschaften|Zeigt die Eigenschaften der verfügbaren Eigenschaften des ausgewählten Knotens im Fenster **Eigenschaften** an.  Alle Eigenschaften sind schreibgeschützt, und nicht jedem Knoten sind Eigenschaften zugeordnet.|  
|Verbindung hinzufügen|Ermöglicht es Ihnen, eine SharePoint\-Website anzugeben, die Sie durchsuchen möchten.  Verfügbar für den Knoten **SharePoint\-Verbindungen** und Unterwebsiteknoten.|  
|In Browser anzeigen|Zeigt die ausgewählte Liste im Webbrowser an.  Dieser Befehl ist für einige Listen unter dem Knoten **Listen** in **Listen und Bibliotheken** verfügbar.|  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Gewusst wie: Hinzufügen oder Entfernen von SharePoint-Verbindungen](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Beschreibt die erforderlichen Schritte zum Hinzufügen einer neuen SharePoint\-Website zum Knoten **SharePoint\-Verbindungen** im **Server\-Explorer**.|  
  
## Siehe auch  
 [Server Explorer](../Topic/Server%20Explorer.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  