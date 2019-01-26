---
title: Überlegungen zu Sandkastenlösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28bdf4e9b116522256606bc9fbbe6b05edb45114
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872975"
---
# <a name="sandboxed-solution-considerations"></a>Überlegungen zu sandkastenlösungen
  *Sandbox-Lösungen* sind ein Feature in Microsoft SharePoint 2010, mit dem Standort Sammlung Benutzer ihre eigenen benutzerdefinierten codelösungen hochladen können. Allgemeine Sandbox-Lösung ist die Benutzer ihre eigenen Webparts hochladen.  
  
 Eine Sandbox SharePoint-Anwendung ausgeführt wird, in einem sicheren, überwachten Prozess, der Zugriff auf einen begrenzten Teil der Webfarm hat. Microsoft SharePoint 2010 verwendet eine Kombination von Features, Projektmappen von Galerien, Lösung, die Überwachung und ein Framework für die Überprüfung auf die um Sandbox-Lösungen zu aktivieren.  
  
## <a name="specify-project-trust-level"></a>Geben Sie die Vertrauensebene für Projekt
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unterstützt die Sandbox-Lösungen durch eine boolesche Eigenschaft namens *Sandkastenlösung*. Diese Eigenschaft kann zu einem beliebigen Zeitpunkt im Projekt festgelegt werden, oder angegeben werden bei der Erstellung des Projekts in der **SharePoint Customization Wizard**.  
  
> [!NOTE]  
>  Ändern der *Sandkastenlösung* Eigenschaft eines Projekts aus, nachdem es erstellt wurde, kann zu Überprüfungsfehlern führen.  
  
 Die Lösung wird eine Lösung Farmbereich betrachtet, wenn die *Sandkastenlösung* -Eigenschaftensatz auf **"false"** , oder Sie wählen die **als farmlösung bereitstellen** Option. Allerdings die Lösung ist anders behandelt als farmlösung Wenn die *Sandkastenlösung* -Eigenschaftensatz auf **"true"** , oder Sie wählen die **als sandkastenlösung bereitstellen** die Option im Assistenten.  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint-Websitehierarchie
 Wie Sandbox-Lösungen zu arbeiten, ist es hilfreich, wissen, dass die SharePoint-Websites, die im Bereich hierarchisch angeordnet sind. Das oberste Element wird als Webfarm bezeichnet, und andere Elemente, die ihm untergeordnet sind:  
  
 Web Farm  
  
 Webanwendung A  
  
 Site Collection A1  
  
 Site A1a  
  
 Webanwendung B  
  
 Site Collection B1  
  
 Site B1a  
  
 Site B1b  
  
 Site Collection B2  
  
 Site B2a  
  
 Wie Sie sehen können, können Webfarmen eine oder mehrere Webanwendungen enthalten, die wiederum eine oder mehrere Websitesammlungen enthalten kann, welche die können Unterwebsites verwenden und so weiter. Änderungen an eine Website Auflistung auswirken, die site der Auflistung vorgenommen und keine anderen. Änderungen, die auf Farmebene Web beeinflussen jedoch alle Websitesammlungen in der Farm.  
  
 Windows SharePoint Services (WSS) 3.0 können Sie zum Bereitstellen von Lösungen nur auf der Farmebene statt, aber [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] können Sie entweder auf der Farmebene statt (farmlösung) oder auf Ebene der Websitesammlung (sandkastenlösung) bereitstellen.  
  
## <a name="why-sandboxed-solutions"></a>Warum Sandbox-Lösungen?
 In WSS 3.0 konnte Lösungen nur auf Farmebene bereitgestellt werden. Dies bedeutete, dass potenziell schädliche oder destabilisierende Lösungen können, die betroffen bereitgestellt werden, die gesamte Webfarm und alle anderen Websitesammlungen und Anwendungen, die darunter ausgeführt. Allerdings können Sie mithilfe von Sandbox-Lösungen können Ihre Lösungen um einen Unterbereich von der Farm, die einer spezifischen Websitesammlung bereitstellen. Um zusätzlichen Schutz bieten, die Assembly der Lösung wird nicht geladen, im Hauptordner [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Prozess (*w3wp.exe*). Stattdessen wird es in einem separaten Prozess geladen (*SPUCWorkerProcess.exe*). Dieser Prozess wird überwacht und implementiert wird, Kontingente und Drosselung, um der Farm von Sandbox-Lösungen zu schützen, die schädliche Aktivitäten ausführen, z. B. das Ausführen der enger Schleifen, die CPU-Zyklen beanspruchen.  
  
## <a name="site-collection-solution-gallery"></a>Lösung sitesammlungs-gallery
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 verfügt über eine Funktion, die sogenannten "Site Collection Solution Gallery." Sie können dieses Feature zugreifen, auf der SharePoint 2010-Zentraladministration oder durch Öffnen der **Websiteaktionen** im Menü auswählen **Standorteinstellungen**, auswählen und dann die **Lösungen** link **Galerien** in der SharePoint-Website. Lösung Kataloge sind-Repositorys von Lösungen, die Websitesammlungs-Administratoren zum Verwalten von Lösungen in ihrer Websitesammlungen aktivieren.  
  
 Der Lösungskatalog ist eine Dokumentbibliothek, die in die Stammwebsite der SharePoint-Website gespeichert. Im Lösungskatalog Websitevorlagen ersetzt und Lösungspakete unterstützt. Wenn ein SharePoint-Lösungspaket (*.wsp*)-Datei wird hochgeladen ist, wird es als Sandbox-Lösung verarbeitet wird.  
  
## <a name="sandboxed-solution-limitations"></a>Beschränkungen von Sandbox-Lösung
 Wenn eine sandkastenlösung bereitgestellt wird, ist das Array von SharePoint-Funktionen zur Verfügung, um alle Sicherheitsrisiken zu reduzieren, die sie möglicherweise beschränkt. Zu diesen Einschränkungen zählen folgende:  
  
- Sandbox-Lösungen müssen eine eingeschränkte Teilmenge der bereitzustellende Lösung-Elemente, die ihnen zur Verfügung. Potenziell anfällig für SharePoint-Projektvorlagen, wie Website-Definitionen und Workflows, sind nicht verfügbar.  
  
- SharePoint Sandkastenlösungscode in einem Prozess ausgeführt (*SPUCWorkerProcess.exe*) getrennt von den Hauptknoten [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] -Anwendungspool (*w3wp.exe*) verarbeiten.  
  
- Zugeordnete Ordner können nicht zum Projekt hinzugefügt werden.  
  
- Typen in der [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] Assembly Microsoft.Office.Server kann nicht in sandkastenlösungen verwendet werden. Darüber hinaus nur Typen in der [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Assembly Microsoft.SharePoint in sandkastenlösungen verwendet werden kann.  
  
  Es ist wichtig zu beachten, dass die Angabe einer SharePoint-Lösung als sandkastenlösung keine Auswirkungen auf SharePoint-Server hat. es nur bestimmt, wie das SharePoint-Projekt bereitgestellt wird, in SharePoint aus [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und welche Assemblys bindet an. Es hat keine Auswirkungen auf die generierte *.wsp* -Datei, und die *.wsp* Datei enthält keine Daten, die direkt mit korreliert die *Sandkastenlösung* Eigenschaft.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funktionen und Elemente in der Sandbox-Lösungen
 Sandbox-Lösungen unterstützen die folgenden Funktionen und die folgenden Elemente:  
  
- Inhaltstypen/Felder  
  
- Benutzerdefinierte Aktionen  
  
- Deklarativer workflows  
  
- Ereignisempfänger  
  
- Feature-Legenden  
  
- Listendefinitionen  
  
- Listeninstanzen  
  
- Modul-Dateien  
  
- Navigation  
  
- *Onet.xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Unterstützung für alle Webparts, die von abgeleitet werden `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Webparts  
  
- WebTemplate Funktionselemente (anstelle von *Webtemp.xml*)  
  
- Visuelle Webparts  
  
  Sandbox-Lösungen unterstützen nicht die folgenden Funktionen und die folgenden Elemente:  
  
- Anwendungsseiten  
  
- Benutzerdefinierte Aktionsgruppe  
  
- Farm-Funktionen  
  
- `HideCustomAction`-Element  
  
- Im Gültigkeitsbereich der Anwendung-Web-Funktionen  
  
- Workflows mit code  
  
## <a name="see-also"></a>Siehe auch
 [Unterschiede zwischen Sandkasten- und farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
