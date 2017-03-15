---
title: "Die ausgew&#228;hlte Verbindung verwendet einen nicht unterst&#252;tzten Datenbankanbieter. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die ausgew&#228;hlte Verbindung verwendet einen nicht unterst&#252;tzten Datenbankanbieter.
Diese Meldung wird angezeigt, wenn Sie Elemente, die den .NET Framework\-Datenanbieter für SQL Server verwenden, von **Server\-Explorer**\/**Datenbank\-Explorer** auf die [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\-Oberfläche ziehen.  
  
 Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] unterstützt nur Datenverbindungen, die den .NET Framework\-Anbieter für SQL Server verwenden.Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server\-Datenbankdatei sind gültig.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie nur Elemente von Datenverbindungen hinzu, die den .NET Framework\-Datenanbieter für SQL Server zu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] verwenden.  
  
## Siehe auch  
 <xref:System.Data.SqlClient>   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/de-de/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Erstellen von Datenanwendungen](../data-tools/creating-data-applications.md)