---
title: "Ausnahmen von Visual Studio-Lebenszyklusrichtlinien | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
caps.handback.revision: 3
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Ausnahmen von Visual Studio-Lebenszyklusrichtlinien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio enthält eine Sammlung von Compilern, Sprachen, Laufzeiten, Umgebungen und anderen Ressourcen, die die Entwicklung für viele Microsoft\-Plattformen ermöglichen. Um Visual Studio\-Kunden die Arbeit zu erleichtern, kann Visual Studio bestimmte Microsoft\-SDKs und andere Microsoft\-Komponenten installieren, die auf diese Microsoft\-Plattformen ausgerichtet sind und sie unterstützen. Die Lizenzierung und Unterstützung dieser Komponenten kann eigenen Bestimmungen und Richtlinien unterliegen.  
  
## Externe Komponenten, die einer anderen Lebenszyklusrichtlinie als der Visual Studio\-Richtlinie unterliegen  
 Die folgende Tabelle enthält die Microsoft\-Plattformkomponenten, die \(je nach Edition der Visual Studio\-Software\) in Visual Studio enthalten sein können und eigenen Supportrichtlinien und Fristen unterliegen.  
  
|PRODUKTFAMILIE|EXTERNER NAME|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 Packet zur Festlegung von Zielversionen \(klassisch\)<br /><br /> .NET 4.5.1 Paket zur Festlegung von Zielversionen \(Store\)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist\-Sprachpakete<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET\-Webstapel](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET\-Web\-API<br /><br /> ASP.NET\-Web\-API 2<br /><br /> ASP.NET\-Webseiten 2<br /><br /> ASP.NET\-Webseiten 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Exchange\-Webdienste|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Updates für diese Komponenten werden über NuGet verteilt und unterliegen nicht den standardmäßigen Microsoft\-Lebenszyklusrichtlinien.  Weitere Informationen finden Sie unter [http:\/\/docs.nuget.org\/](http://docs.nuget.org/).|JSON\-Webtokenhandler für Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Open XML SDK|  
|[Online Services\-Richtlinie](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Ads SDK|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint\-Clientkomponente<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation \(WIF\)\-Erweiterungen|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> Siehe auch: [http:\/\/support.microsoft.com\/gp\/lifean45](http://support.microsoft.com/gp/lifean45)|Silverlight 5\-Laufzeit<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|CLR\-Typen des SQL\-Systems \(SQL Server 2008 R2\)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx \(DACFramework\)<br /><br /> SMO \(SharedManagementObjects\)<br /><br /> SQL\-Befehlszeilenprogramme<br /><br /> SQL\-Sprachdienst – IntelliSense \(TSQLLanguageService\)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client \(Sqlncli\)<br /><br /> SQL Server Express 2012 SP1<br /><br /> CLR\-Typen des SQL\-Systems \(SQL Server 2012\)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx \(DACFramework\)<br /><br /> SMO \(SharedManagementObjects\)<br /><br /> SQL\-Befehlszeilenprogramme<br /><br /> SQL\-Sprachdienst – IntelliSense \(TSQLLanguageService\)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client \(Sqlncli\)<br /><br /> SQL Server Express 2014<br /><br /> CLR\-Typen des SQL\-Systems \(SQL Server 2014\)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows\-Webdienste für Windows Server 2008|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|Windows 7 SDK|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> Windows Library für JavaScript \(WinJS\)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> Siehe auch: [Online\-Lebenszyklusrichtlinie](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Azure Mobile Services SDK<br /><br /> Microsoft Azure Mobile Services Tools|