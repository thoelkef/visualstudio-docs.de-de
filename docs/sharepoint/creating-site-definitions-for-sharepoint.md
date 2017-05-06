---
title: "Erstellen von Websitedefinitionen f&#252;r SharePoint"
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
  - "SharePoint-Entwicklung in Visual Studio, Websitedefinitionen"
  - "Websitedefinitionen [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Erstellen von Websitedefinitionen f&#252;r SharePoint
  Mit dem SharePoint\-Projekt "Websitedefinition" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] können Sie eine *Websitedefinition* erstellen, die als Grundlage für eine neue SharePoint\-Website fungiert.  Diese Definitionen bestimmen nicht nur die Darstellung und das Verhalten der SharePoint\-Website, sondern auch den Standardinhalt und die Funktionen.  In der Definition können Sie vorkonfigurierte Listen, Inhaltstypen, Ereignisempfänger, Bilder und andere Elemente setzen.  SharePoint schließt einige Websitedefinitionen wie BLOG, beispielsweise ein.  Wenn Sie auf Grundlage der Websitedefinition BLOG eine Website erstellen, enthält diese Website die Listen, Webparts und anderen Elemente, die eine Blogwebsite erfordert.  
  
 Weitere Informationen zu Websitedefinitionen, Sie finden. [Site\-Vorlagen und Definitionen](http://go.microsoft.com/fwlink/?LinkId=179134)  
  
## Websitedefinitionsprojekte  
 Websitedefinitionsprojekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stellen nur die grundlegenden Dateien bereit, die eine SharePoint\-Website benötigt, aber keine Standardfunktionen.  Sie müssen Dateien und Inhalt hinzufügen, um die gewünschten Funktionen bereitzustellen.  Sie können die Website manuell erstellen, indem Sie die benötigten Dateien erstellen und hinzufügen.  
  
## Funktionsanheftung  
 Ein Vorteil beim Erstellen von Websitedefinitionen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] besteht darin, dass diese automatisch die *Funktionsanheftung* verwenden.  Bei der Funktionsanheftung wird eine Funktion einer Websitedefinition hinzugefügt, anstatt die Funktion in der Websitedefinition selbst einzubetten.  Hierdurch können Sie die Funktion einer beliebigen erstellten Website hinzufügen, indem Sie die Websitedefinition verwenden, ohne die ursprüngliche Websitedefinition zu ändern.  Weitere Informationen finden Sie unter [Funktionsanheftung](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## Komponenten von Websitedefinitionsprojekten  
 Wenn Sie eine Websitedefinitionslösung erstellen, werden dem Knoten **SiteDefinition** die folgenden Standarddateien hinzugefügt.  
  
|Dateiname|**Beschreibung**|  
|---------------|----------------------|  
|default.aspx|Die ASPX\-Standardhomepage für die neue SharePoint\-Website.|  
|onet.xml|Gibt die Konfiguration der neuen Website, die Komponenten der Websitedefinitionsvorlage und das Standardverhalten an.  Diese Einstellungen können folgende Attribute einschließen: die Inhaltstypen, die aktiviert werden, die Standardlistenansichten, Dokumentvorlagendateien und in der Website enthaltene Webparts.  Standardmäßig sind im Abschnitt `Modules` die Dateien, die der SharePoint\-Website hinzugefügt werden sollen, sowie ihre Konfiguration aufgeführt.|  
|webtemp\_*SiteDefinitionName*.xml|Gibt die Websitedefinitionskonfigurationen an, die im Abschnitt **Vorlagenauswahl** der Seite **Neue SharePoint\-Website** angezeigt werden.|  
  
 Standardmäßig werden alle Websitedefinitionen im Ordner *drive:*\\Programme\\Gemeinsame Dateien\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\SiteTemplates gespeichert.  Jede Websitedefinition befindet sich in einem eigenen Unterordner.  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Websitedefinition](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Enthält schrittweise Anweisungen für die Erstellung eines einfachen Sitedefinitionsprojekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Gewusst wie: Erstellen Sie eine benutzerdefinierte Websitedefinition und einer Konfiguration](http://go.microsoft.com/fwlink/?LinkId=183309)|Beschreibt, wie eine benutzerdefinierte Websitedefinition in SharePoint erstellt wird, indem eine vorhandene Websitedefinition kopiert wird, und die Kopie dann geändert wird.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Beschreibt die ursprüngliche Datei, in der die im Abschnitt **Vorlagenauswahl** der Seite **Neue SharePoint\-Website** verfügbaren Websitedefinitionen angegeben werden.|  
|[Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)|Beschreibt, wie die SharePoint\-Lösungen auf die globale Verwendung vorbereitet werden.|  
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Teile einer SharePoint\-Seite erstellen können, die Benutzer ändern können.|  
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Sie wiederverwendbare Steuerelemente erstellen können, die in Anwendungsseiten und Webparts ausgeführt werden.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Beschreibt die Verwendung des Designers, der angezeigt wird, wenn Sie im Projekt eine Webseite öffnen.|  
|[ASP.NET Web Pages\-Übersicht](http://go.microsoft.com/fwlink/?LinkId=178726)|Stellt allgemeine Informationen zur Struktur von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Webseiten bereit, wie Seiten von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] verarbeitet werden, und wie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Seiten Markup anzeigen, das XHTML\-Standards entspricht.|  
|[ASP.NET\-Webseiten\-Syntax](http://go.microsoft.com/fwlink/?LinkId=178727)|Beschreibt die Markupelemente, aus denen eine ASP.NET\-Seite besteht.|  
|[Programmieren von ASP.NET\-Webseiten](http://go.microsoft.com/fwlink/?LinkId=178728)|Enthält Informationen zum Erstellen von Ereignishandlern auf [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Seiten und zur Verwendung von Clientskripts.|  
|[Programmierung in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Beschreibt die Verwendung des in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] verfügbaren verwalteten Objektmodells.|  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  