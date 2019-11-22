---
title: Visual Studio Lifecycle Policy Exceptions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6db11d583818f1ea63c490cd8f588cb005b50a8d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295933"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Ausnahmen von Visual Studio-Lebenszyklusrichtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio enthält eine Sammlung von Compilern, Sprachen, Laufzeiten, Umgebungen und anderen Ressourcen, die die Entwicklung für viele Microsoft-Plattformen ermöglichen. Um Visual Studio-Kunden die Arbeit zu erleichtern, kann Visual Studio bestimmte Microsoft-SDKs und andere Microsoft-Komponenten installieren, die auf diese Microsoft-Plattformen ausgerichtet sind und sie unterstützen. Die Lizenzierung und Unterstützung dieser Komponenten kann eigenen Bestimmungen und Richtlinien unterliegen.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Externe Komponenten, die einer anderen Lebenszyklusrichtlinie als der Visual Studio-Richtlinie unterliegen  
 Die folgende Tabelle enthält die Microsoft-Plattformkomponenten, die (je nach Edition der Visual Studio-Software) in Visual Studio enthalten sein können und eigenen Supportrichtlinien und Fristen unterliegen.  
  
|PRODUKTFAMILIE|EXTERNER NAME|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 Packet zur Festlegung von Zielversionen (klassisch)<br /><br /> .NET 4.5.1 Paket zur Festlegung von Zielversionen (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist-Sprachpakete<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET-Webstapel](https://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET-Web-API<br /><br /> ASP.NET-Web-API 2<br /><br /> ASP.NET-Webseiten 2<br /><br /> ASP.NET-Webseiten 3|  
|[Entity Framework 6](https://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](https://go.microsoft.com/fwlink/?LinkId=328950)|Exchange-Webdienste|  
|[Microsoft OWIN](https://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Updates für diese Komponenten werden über NuGet verteilt und unterliegen nicht den standardmäßigen Microsoft-Lebenszyklusrichtlinien.  Weitere Informationen finden Sie unter [http://docs.nuget.org/](https://docs.microsoft.com/nuget/).|JSON-Webtokenhandler für Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](https://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[Online Services-Richtlinie](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint-Clientkomponente<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation (WIF)-Erweiterungen|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />Weitere Informationen: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5-Laufzeit<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|CLR-Typen des SQL-Systems (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL-Befehlszeilenprogramme<br /><br /> SQL-Sprachdienst – IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> CLR-Typen des SQL-Systems (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL-Befehlszeilenprogramme<br /><br /> SQL-Sprachdienst – IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> CLR-Typen des SQL-Systems (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](https://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows-Webdienste für Windows Server 2008|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> Windows Library für JavaScript (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> See also: [Online Lifecycle Policy](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Azure Mobile Services SDK<br /><br /> Microsoft Azure Mobile Services Tools|