---
title: "&#220;berlegungen zu Sandkastenl&#246;sungen"
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
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Farmlösungen [SharePoint-Entwicklung in Visual Studio]"
  - "Sandkastenlösungen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Farmlösungen"
  - "SharePoint-Entwicklung in Visual Studio, Sandkastenlösungen"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &#220;berlegungen zu Sandkastenl&#246;sungen
  *Sandkastenlösungen* sind eine Funktion in Microsoft SharePoint 2010, die es Websiteauflistungsbenutzern ermöglicht, eigene benutzerdefinierte Codeprojektmappen hochzuladen.  Bei einer gängigen Sandkastenlösung laden Benutzer eigene Webparts hoch.  
  
 Eine SharePoint\-Sandkastenanwendung wird in einem sicheren überwachten Prozess ausgeführt, der Zugriff auf einen beschränkten Teil der Webfarm hat.  Microsoft SharePoint 2010 aktiviert Sandkastenlösungen mithilfe einer Kombination aus Funktionen, Lösungskatalogen, Lösungsüberwachung und einem Validierungsframework.  
  
## Angeben der Projektvertrauensebene  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unterstützt Sandkastenlösungen durch eine boolesche Projekteigenschaft mit dem Namen *Sandboxed Solution*.  Diese Eigenschaft kann im Projekt jederzeit festgelegt oder dann angegeben werden, wenn Sie das Projekt im **Assistenten zum Anpassen von SharePoint** erstellen.  
  
> [!NOTE]  
>  Wenn die Eigenschaft *Sandboxed Solution* eines Projekts nach seiner Erstellung geändert wird, kann dies Validierungsfehler verursachen.  
  
 Die Projektmappe wird eine Farm als Projektmappe, wenn die *Sandboxed Solution*\-Eigenschaft auf **false** festgelegt wird, oder Sie die Option **Als Farmlösung bereitstellen** auswählen.  Allerdings wird die Projektmappe als mit einer Farmlösung behandelt, wenn die *Sandboxed Solution*\-Eigenschaft auf **true** festgelegt wird, oder Sie die Option **Als Sandkastenlösung bereitstellen** im Assistenten auswählen.  
  
## SharePoint\-Websitehierarchie  
 Die Funktionsweise von Sandkastenlösungen wird verständlicher mit dem Wissen, dass SharePoint\-Websitebereiche hierarchisch sind.  Das oberste Element wird als Webfarm bezeichnet, und andere Elemente sind diesem Element untergeordnet:  
  
 Webfarm  
  
 Webanwendung A  
  
 Websiteauflistung A1  
  
 Website A1a  
  
 Webanwendung B  
  
 Websiteauflistung B1  
  
 Website B1a  
  
 Website B1b  
  
 Websiteauflistung B2  
  
 Website B2a  
  
 Webfarmen können eine oder mehrere Webanwendungen enthalten, die wiederum eine oder mehrere Websiteauflistungen enthalten können, die über Unterwebsites verfügen können, usw.  Änderungen an einer Websiteauflistung wirken sich nicht auf andere Websiteauflistungen aus.  Änderungen auf Webfarmebene wirken sich jedoch auf alle Websiteauflistungen der Webfarm aus.  
  
 Mit Windows SharePoint Services 3.0 \(WSS\) können Sie Lösungen nur auf Farmebene bereitstellen, aber mit [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ist die Bereitstellung entweder auf Farmebene \(Farmlösung\) oder auf Websiteauflistungsebene \(Sandkastenlösung\) möglich.  
  
## Gründe für die Verwendung von Sandkastenlösungen  
 In WSS 3.0 konnten Lösungen nur auf Farmebene bereitgestellt werden.  Das bedeutet, dass potenziell schädliche oder destabilisierende Lösungen bereitgestellt werden konnten, die sich auf die gesamte Webfarm sowie auf alle weiteren Websiteauflistungen und Anwendungen auswirkten, die darunter ausgeführt wurden.  Bei Sandkastenlösungen können Sie Lösungen jedoch in einem Unterbereich der Farm, einer spezifischen Websiteauflistung, bereitstellen.  Um zusätzlichen Schutz zu bieten, wird die Assembly der Lösung nicht im [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]\-Hauptprozess \(w3wp.exe\) geladen.  Stattdessen wird sie in einem separaten Prozess geladen \(SPUCWorkerProcess.exe\).  Dieser Prozess wird überwacht und implementiert Kontingente und Einschränkungen, um die Farm vor Sandkastenlösungen zu schützen, die schädliche Aktivitäten ausführen, z. B. geschlossene Schleifen, die CPU\-Zyklen verbrauchen.  
  
## Lösungskatalog für Websiteauflistungen  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 beinhaltet eine Funktion, die bekannt als "Siteauflistungsprojektmappenkatalog." Sie können auf diese Funktion zugreifen der Seite Zentraladministration von SharePoint oder indem Sie das Menü **Websiteaktionen** öffnen auswählen, **Websiteeinstellungen**, und dann den Link **Projektmappen** unter  **Galerien** in der SharePoint\-Website auswählen.  Lösungskataloge sind Repositorys von Lösungen, die es Websiteauflistungsadministratoren ermöglichen, Lösungen in ihren Websiteauflistungen zu verwalten.  
  
 Der Lösungskatalog ist eine im Stammweb der SharePoint\-Website gespeicherte Dokumentbibliothek.  Der Lösungskatalog ersetzt Websitevorlagen und unterstützt Lösungspakete.  Eine hochgeladene SharePoint\-Lösungspaketdatei \(.wsp\) wird als Sandkastenlösung verarbeitet.  
  
## Einschränkungen von Sandkastenlösungen  
 Wenn eine Sandkastenlösung bereitgestellt wird, ist das verfügbare Array von SharePoint\-Funktionen beschränkt, um potenzielle Sicherheitslücken zu verringern.  Einige dieser Beschränkungen schließen Folgendes ein:  
  
-   Für Sandkastenlösungen steht eine eingeschränkte Teilmenge von zur Bereitstellung geeigneter Lösungselemente zur Verfügung.  Potenziell anfällige SharePoint\-Projektvorlagen, z. B. Websitedefinitionen und Workflows, sind nicht verfügbar.  
  
-   SharePoint\-führt Sandkastenlösungscode in einem Prozess \(SPUCWorkerProcess.exe\) aus, der vom Hauptprozess des [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]\-Anwendungspools \(w3wp.exe\) getrennt ist.  
  
-   Zugeordnete Ordner können dem Projekt nicht hinzugefügt werden.  
  
-   Typen in der [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]\-Assembly Microsoft.Office.Server können nicht in Sandkastenlösungen verwendet werden.  Darüber hinaus können nur Typen in der [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]\-Assembly Microsoft.SharePoint in Sandkastenlösungen verwendet werden.  
  
 Beachten Sie, dass das Festlegen einer SharePoint\-Lösung als Sandkastenlösung keine Auswirkungen auf SharePoint\-Server hat. Hierdurch wird lediglich bestimmt, wie das SharePoint\-Projekt von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] in SharePoint bereitgestellt wird und an welche Assemblys es gebunden wird.  Die generierte WSP\-Datei wird dadurch nicht beeinflusst. Sie enthält keine Daten, die mit der Eigenschaft *Sandboxed Solution* zusammenhängen.  
  
## Funktionen und Elemente in Sandkastenlösungen  
 Sandkastenlösungen unterstützen die folgenden Funktionen und Elemente:  
  
-   Inhaltstypen\/Felder  
  
-   Benutzerdefinierte Aktionen  
  
-   Deklarative Workflows  
  
-   Ereignisempfänger  
  
-   Ausgehende Funktionsaufrufe  
  
-   Listendefinitionen  
  
-   Listeninstanzen  
  
-   Module\/Dateien  
  
-   Navigation  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Unterstützung für alle von `System.Web.UI.WebControls.WebParts.WebPart` abgeleiteten Webparts  
  
-   Webparts  
  
-   WebTemplate\-Funktionselemente \(anstelle von Webtemp.xml\)  
  
-   Visuelle Webparts  
  
 Sandkastenlösungen bieten keine Unterstützung für die folgenden Funktionen und Elemente:  
  
-   Anwendungsseiten  
  
-   Benutzerdefinierte Aktionsgruppe  
  
-   Funktionen mit dem Gültigkeitsbereich Farm  
  
-   `HideCustomAction`\-Element  
  
-   Funktionen mit dem Gültigkeitsbereich Webanwendung  
  
-   Workflows mit Code  
  
## Siehe auch  
 [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  