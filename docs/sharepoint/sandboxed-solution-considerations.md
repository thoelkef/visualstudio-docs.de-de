---
title: "Überlegungen zu Sandkastenlösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2dcf8040217a13688dc1ff33183f237f0f58bbcf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *Sandkastenlösungen* sind eine Funktion in Microsoft SharePoint 2010, mit dem Standort Auflistung Benutzer ihre eigenen benutzerdefinierten codelösungen hochladen können. Eine allgemeine sandkastenlösung ist Benutzer ihre eigenen Webparts hochladen.  
  
 Eine Sandbox SharePoint-Anwendung ausgeführt wird, in einem sicheren, überwachten Prozess, der Zugriff auf einen begrenzten Teil der Webfarm hat. Microsoft SharePoint 2010 verwendet eine Kombination von Funktionen, Projektmappen Galerien Lösung überwachen und eine Validierungsframework sandkastenlösungen zu aktivieren.  
  
## <a name="specifying-project-trust-level"></a>Projektvertrauensebene angeben  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]unterstützt, die über eine boolesche Projekteigenschaft sandkastenlösungen aufgerufen *Sandkastenlösung*. Diese Eigenschaft kann festgelegt werden, zu einem beliebigen Zeitpunkt im Projekt oder angegeben werden beim Erstellen des Projekts in der **Assistent zum Anpassen von SharePoint**.  
  
> [!NOTE]  
>  Ändern der *Sandkastenlösung* Eigenschaft eines Projekts nach seiner Erstellung Überprüfungsfehler verursachen.  
  
 Die Lösung wird eine Lösung Farmbereich betrachtet, wenn die *Sandkastenlösung* -Eigenschaftensatz auf **"false"** , oder Sie wählen Sie die **als farmlösung bereitstellen** Option. Allerdings die Projektmappe wird anders behandelt als farmlösung Wenn die *Sandkastenlösung* -Eigenschaftensatz auf **"true"** , oder Sie wählen Sie die **bereitstellen als sandkastenlösung** die Option im Assistenten.  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint-Site-Hierarchie  
 Um zu verstehen, wie sandkastenlösungen arbeiten können, um wissen, dass SharePoint-Websites, die im Bereich hierarchisch angeordnet sind. Das oberste Element wird als der Webfarm bezeichnet, und andere Elemente, die ihm untergeordnet sind:  
  
 Webfarm  
  
 Web-Anwendung ein  
  
 Standort Auflistung A1  
  
 Website-A1a  
  
 Webanwendung B  
  
 Standort Auflistung B1  
  
 Standort B1a  
  
 Standort B1b  
  
 Die Auflistung B2 Standort  
  
 Website-B2a  
  
 Wie Sie sehen können, darf Webfarmen eine oder mehrere Webanwendungen, die wiederum einen oder mehrere Websitesammlungen enthalten können, welche die Unterwebsites haben können, und so weiter. Änderungen an einem Standort Auflistung wirkt sich nur die Websitesammlung vorgenommen und keine anderen. Allerdings auf Farmebene Web vorgenommene Änderungen alle Websitesammlungen in der Farm.  
  
 Windows SharePoint Services (WSS) 3.0 können Sie nur auf Farmebene, Lösungen bereitstellen, aber [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] können Sie auf die Farmebene beziehen (farmlösung) oder der Ebene der Websitesammlung (sandkastenlösung) bereitstellen.  
  
## <a name="why-sandboxed-solutions"></a>Warum Sandkastenlösungen?  
 WSS 3.0 konnte Lösungen nur auf Farmebene bereitgestellt werden. Dies bedeutet, dass potenziell schädliche oder zur Destabilisierung Lösungen bereitgestellt werden konnte, die betroffenen der gesamten Webfarm und alle anderen Websitesammlungen und Anwendungen, die darunter ausgeführt. Mithilfe von sandkastenlösungen können Sie jedoch Ihre Lösungen, die einem Unterbereich der Farm eine bestimmte Websitesammlung bereitstellen. Um zusätzlichen Schutz zu gewährleisten, die Assembly der Lösung wurde nicht geladen, in der Main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] -Prozess (w3wp.exe). Stattdessen wird es in einem separaten Prozess (SPUCWorkerProcess.exe) geladen. Dieser Prozess wird überwacht und implementiert wird, Kontingente und Einschränkungen, um der Farm sandkastenlösungen zu schützen, die schädliche Aktivitäten ausführen, z. B. das Ausführen von enger Schleifen, die CPU-Zyklen beanspruchen.  
  
## <a name="site-collection-solution-gallery"></a>Katalog der Websitesammlung-Lösung  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]2010 ist eine Funktion, die sogenannten "Site Auflistung Solution Gallery." Sie können auf dieses Feature zuzugreifen, über die Seite "SharePoint 2010-Zentraladministration" oder durch Öffnen der **Websiteaktionen** im Menü auswählen **Standorteinstellungen**, und drücken Sie dann die **Lösungen** link **Galerien** in der SharePoint-Website. Lösung Kataloge sind Repositorys von Lösungen, die Websitesammlungs-Administratoren zum Verwalten von Lösungen in ihren Websitesammlungen aktivieren.  
  
 Solution Gallery ist eine Dokumentbibliothek in der Stammwebsite der SharePoint-Website gespeichert. Solution Gallery ersetzt Websitevorlagen und Lösungspakete unterstützt. Wenn eine SharePoint-Lösung-Paketdatei (.wsp) hochgeladen wird, wird er als sandkastenlösung verarbeitet.  
  
## <a name="sandboxed-solution-limitations"></a>Sandkastenlösung Einschränkungen  
 Wenn eine sandkastenlösung bereitgestellt wird, ist das Array von SharePoint-Funktionen zur Verfügung, um alle Sicherheitsrisiken zu reduzieren, die sie möglicherweise beschränkt. Diese Einschränkungen umfassen Folgendes:  
  
-   Sandkastenlösungen haben eine eingeschränkte Teilmenge eines bereitstellbare Projektmappen-Elemente, die ihnen zur Verfügung stehen. Potenziell anfällig für SharePoint-Projektvorlagen, wie Websitedefinitionen und Workflows, sind nicht verfügbar.  
  
-   SharePoint-führt Sandkastenlösungscode in einem Prozess (SPUCWorkerProcess.exe) aus dem Hauptknoten [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] anwendungspoolprozess (w3wp.exe).  
  
-   Anzeige zugeordneter Ordner können nicht zum Projekt hinzugefügt werden.  
  
-   Typen in der [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] Assembly Microsoft.Office.Server kann nicht in sandkastenlösungen verwendet werden. Darüber hinaus nur Typen in der [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Assembly Microsoft.SharePoint in sandkastenlösungen verwendet werden kann.  
  
 Es ist wichtig zu beachten, dass die Angabe einer SharePoint-Lösung als sandkastenlösung auf SharePoint-Server keine Auswirkungen hat. er nur bestimmt, wie die SharePoint-Projekt bereitgestellt wird, in SharePoint aus [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und welche Assemblys es gebunden wird. Es hat keine Auswirkungen auf die generierten WSP-Datei, und die WSP-Datei enthält keine Daten, die direkt mit korreliert die *Sandkastenlösung* Eigenschaft.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funktionen und Elementen in Sandkastenlösungen  
 Sandkastenlösungen unterstützen die folgenden Funktionen und die folgenden Elemente:  
  
-   Inhaltstypen/Felder  
  
-   Benutzerdefinierte Aktionen  
  
-   Deklarativer workflows  
  
-   Ereignisempfänger  
  
-   Funktionsaufrufe  
  
-   Listendefinitionen  
  
-   Instanzen auflisten  
  
-   Modul-Dateien  
  
-   Navigation  
  
-   onet.Xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Unterstützung für alle Webparts, die von abgeleitet werden`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Webparts  
  
-   WebTemplate-Funktionselemente (anstelle von Webtemp.xml)  
  
-   Visuelle Webparts  
  
 Sandkastenlösungen unterstützen nicht die folgenden Funktionen und die folgenden Elemente:  
  
-   Anwendungsseiten  
  
-   Benutzerdefinierte Aktion Gruppe  
  
-   Farm-Funktionen  
  
-   `HideCustomAction`-Element  
  
-   Im Bereich der Anwendung Web-Funktionen  
  
-   Workflows mit code  
  
## <a name="see-also"></a>Siehe auch  
 [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  