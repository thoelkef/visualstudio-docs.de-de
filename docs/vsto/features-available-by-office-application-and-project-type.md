---
title: "Verf&#252;gbare Funktionen nach Office-Anwendung und Projekttyp | Microsoft Docs"
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
  - "Add-Ins [Office-Entwicklung in Visual Studio]"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio]"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio]"
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Verfügbare Features"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Verfügbare Features"
  - "Office-Entwicklung in Visual Studio, Funktionen"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Verfügbare Features"
  - "Menüband [Office-Entwicklung in Visual Studio]"
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Verf&#252;gbare Funktionen nach Office-Anwendung und Projekttyp
  Visual Studio verfügt über mehrere Arten von Projektvorlagen, die unterschiedliche Geschäftsszenarien für Microsoft Office\-Anwendungen unterstützen, z. B.:  
  
-   Anpassungen auf Dokumentebene  
  
-   VSTO\-Add\-Ins  
  
 Nicht alle Anwendungen können jeden Projekttyp verwenden.  Beispielsweise sind Projekte auf Dokumentebene nur für Microsoft Office Word und Microsoft Office Excel verfügbar.  Ebenso sind einige Features nur für bestimmte Projekt\- oder Anwendungstypen verfügbar.  Der Aktionsbereich ist beispielsweise nur in Projekten auf Dokumentebene verfügbar, und Menübanderweiterungen stehen nur für einige Anwendungen zur Verfügung.  Weitere Informationen zu den unterschiedlichen Projekttypen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Office\-Projektvorlagen sind nur in einigen Editionen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügbar.  Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Lösungen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## Für Microsoft Office\-Anwendungen verfügbare Projekttypen  
 In der folgenden Tabelle sind die Anwendungen aufgeführt, die Sie für die einzelnen Projekttypen verwenden können.  
  
|Projekttypen|Microsoft Office\-Anwendung|  
|------------------|---------------------------------|  
|Anpassungen auf Dokumentebene|Excel<br /><br /> Word|  
|VSTO\-Add\-Ins|Excel<br /><br /> InfoPath \(nur InfoPath 2013 und InfoPath 2010\)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## In Projekttypen verfügbare Features  
 In der folgenden Tabelle ist aufgeführt, für welche Projekttypen das jeweilige Feature bereitgestellt wird.  
  
|Funktion|Projekttypen, die das Feature bereitstellen|Weiterführende Themen|  
|--------------|-------------------------------------------------|---------------------------|  
|Aktionsbereich|Projekte auf Dokumentebene|[Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)|  
|ClickOnce\-Bereitstellung:|VS\-Projekte und Projekte auf Dokumentebene|[Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)|  
|Benutzerdefinierte Aufgabenbereiche|VSTO\-Add\-In\-Projekte für die folgenden Anwendungen:<br /><br /> -   Excel<br />-   InfoPath \(nur InfoPath 2013 und InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Word|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
|Benutzerdefinierte XML\-Teile|Projekte auf Dokumentebene<br /><br /> Projekte auf Anwendungsebene für die folgenden Anwendungen:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|[Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)|  
|Datencache|Projekte auf Dokumentebene|[Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)|  
|Verfügbarmachen eines Objekts in einem VSTO\-Add\-In für andere Microsoft Office\-Projektmappen|VSTO\-Add\-In\-Projekte|[Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Folgende Hoststeuerelemente:<br /><br /> -   Diagramm<br />-   ListObject<br />-   NamedRange<br />-   ContentControl\-Elemente<br />-   Lesezeichen|Projekte auf Dokumentebene<br /><br /> VSTO\-Add\-In\-Projekte für Word und Excel|[Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)|  
|Folgende Hoststeuerelemente:<br /><br /> -   XMLMappedRange<br />-   XMLNode<br />-   XMLNodes|Projekte auf Dokumentebene|[Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)|  
|Bereitstellung von mehreren Projekten|Projekte auf Dokumentebene<br /><br /> VSTO\-Add\-In\-Projekte|[Exemplarische Vorgehensweise: Bereitstellen mehrerer Office\-Lösungen in einem einzigen ClickOnce\-Installationsprogramm](http://msdn.microsoft.com/de-de/051223c0-4082-4799-b78b-a4763a9def55)|  
|Outlook\-Formularbereiche|VSTO\-Add\-In\-Projekte für Outlook|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|  
|Aktionen nach der Bereitstellung|Projekte auf Dokumentebene<br /><br /> VSTO\-Add\-In\-Projekte|[Exemplarische Vorgehensweise: Kopieren eines Dokuments auf den Computer des Endbenutzers nach einer ClickOnce\-Installation](http://msdn.microsoft.com/de-de/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Menübandanpassungen|Projekte auf Dokumentebene<br /><br /> VSTO\-Add\-In\-Projekte für die folgenden Anwendungen:<br /><br /> -   Excel<br />-   InfoPath \(nur InfoPath 2013 und InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Projekt<br />-   Visio<br />-   Word|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
|Visueller Dokumentdesigner|Projekte auf Dokumentebene|[Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## Siehe auch  
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  