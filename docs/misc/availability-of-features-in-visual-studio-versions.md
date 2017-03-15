---
title: "Verf&#252;gbarkeit von Funktionen in Visual Studio-Versionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, Verfügbarkeit von Funktionen"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Verf&#252;gbarkeit von Funktionen in Visual Studio-Versionen
In der folgenden Tabelle ist angegeben, ob bestimmte Funktionen in den aufgeführten Versionen von Visual Studio Professional unterstützt werden.  
  
-   "ja" bedeutet, dass die Visual Studio\-Version die Funktion enthält.  
  
-   "Hinzufügen" bedeutet, dass die Visual Studio\-Version die Funktion nicht enthält, diese jedoch verfügbar ist, und dass Sie weitere Informationen erhalten können, indem Sie auf den Link klicken.  
  
-   "nein" bedeutet, dass die Visual Studio\-Version die Funktion nicht enthält.  
  
||Visual Studio 2010<br /><br /> und<br /><br /> Visual Studio 2010 SP1|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
|-|-----------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|Unterstützte .NET Framework\-Versionen|2.0, 3.0, 3.5 SP1, 4|2.0, 3.0, 3.5 SP1, 4, 4.5|2.0, 3.0, 3.5 SP1, 4, 4.5, 4.5.1|  
|Lokaler Webserver|Ja|Ja|Ja|  
|SQL Server Express|2008|2008|2008|  
|Herstellen einer Verbindung zu SQL Server\-Versionen per Server\-Explorer|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET AJAX <sup>1</sup>|Ja|Ja|Ja|  
|ASP.NET Model View Controller|Ja|Ja|Ja|  
|ASP.NET Dynamic Data|Ja|Ja|Ja|  
|MSBuild|Ja|Ja|Ja|  
|ADO.NET Entity Framework|Ja|Ja|Ja|  
|ADO.NET Data Services|Ja|Ja|Ja|  
|Microsoft Azure\-Tools|Hinzufügen|Hinzufügen||  
|Intelligente Geräte|Nein|Nein||  
|Parallele Computervorgänge|ja <sup>2</sup>|Ja|Ja|  
|Windows Communication Foundation|Ja|Ja|Ja|  
|Windows Presentation Foundation|Ja|Ja|Ja|  
|.NET Rich Internet Application\-Dienste|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=230768)|Ja|Ja|  
|Silverlight 1|Ja|Ja|Ja|  
|Silverlight 2|Nein|Ja|Ja|  
|Silverlight 3|Ja|Ja|Ja|  
|Silverlight 4|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=153710)|Ja|Ja|  
|Silverlight 5|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=215392), nur SP1.|Ja|Ja|  
|IronPython|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183863)|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183863)|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183864)|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183864)|[Hinzufügen](http://go.microsoft.com/fwlink/?LinkID=183864)|  
|Visual Studio\-Tools für Office|ja <sup>4</sup><br /><br /> \(Office 2007, Office 2010\)|Ja <sup>4</sup>\(Office 2010\)|Ja <sup>4</sup>\(Office 2013\)|  
|Berichtsprojekte|Ja|Ja|Ja|  
|Berichts\-Assistent|Ja|Ja|Ja|  
|Language\-Integrated Query \(LINQ\)|Ja|Ja|Ja|  
|SharePoint\-Entwicklung|Ja, für SharePoint 2010|Ja, für SharePoint 2010|Ja, für SharePoint 2013|  
|.NET Framework 4 Client Profile\-Unterstützung|Ja|Nein|Nein|  
  
1.  ASP.NET AJAX:  
  
     Serverseitig: Die Steuerelemente sind in ASP.NET 3.5 enthalten und in Visual Studio und Visual Web Developer bereits in der **Toolbox** vorhanden.  Wenn Sie eine frühere Version von ASP.NET verwenden, z. B. ASP.NET 2.0, können Sie die [ASP.NET AJAX\-Erweiterungen herunterladen](http://go.microsoft.com/fwlink/?LinkID=75360).  
  
     Clientseitig: Die clientseitige ASP.NET AJAX\-Bibliothek ist in ASP.NET 3.5 SP1 enthalten.  
  
2.  Parallele Computervorgänge  
  
     Parallel Extensions enthält die Task Parallel Library \(TPL\), Parallel LINQ \(PLINQ\) und die Parallelitätsdatenstrukturen. Diese Komponenten sind in .NET Framework 4 enthalten.  Die entsprechenden Bibliotheken für systemeigene C\+\+\-Entwicklung sind die Concurrency Runtime und die Agents Library, die in Visual Studio 2010 enthalten sind.  Die Profiler\- und Debuggererweiterungen sind ebenfalls in Visual Studio 2010 enthalten.  
  
3.  IronPython und IronRuby:  
  
     Auf den CodePlex\-Websites für IronPython und IronRuby sind mehrere Versionen verfügbar.  Wählen Sie die zutreffende Version für Ihre Umgebung aus.  Die Mindestanforderung für beide Sprachen ist .NET Framework 2.0 SP1.  
  
4.  Visual Studio Tools für Office \(VSTO\)\-Kompatibilität und Add\-In\-Funktionalität:  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |Dokumentebene|Word 2007, Word 2010, Excel 2007, Excel 2010|Word 2010, Excel 2010|Word 2013, Excel 2013|  
    |Anwendungsebene|Word 2007, Word 2010, Excel 2007, Excel 2010, InfoPath 2007, InfoPath 2010, Outlook 2007, Outlook 2010, PowerPoint 2007, PowerPoint 2010, Visio 2007, Visio 2010, Project 2007, Project 2010|Word 2010, Excel 2010, InfoPath 2010, Outlook 2010, PowerPoint 2010, Visio 2010, Project 2010|Word 2013, Excel 2013, InfoPath 2013, Outlook 2013, PowerPoint 2013, Visio 2013, Project 2013|