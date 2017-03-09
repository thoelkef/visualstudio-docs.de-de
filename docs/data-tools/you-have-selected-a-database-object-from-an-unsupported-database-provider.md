---
title: "Sie haben ein Datenbankobjekt von einem nicht unterst&#252;tzten Datenbankanbieter ausgew&#228;hlt | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Sie haben ein Datenbankobjekt von einem nicht unterst&#252;tzten Datenbankanbieter ausgew&#228;hlt
Der [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) unterstützt nur den .NET Framework\-Datenbankanbieter für SQL Server \(<xref:System.Data.SqlClient>\).Obwohl Sie auf **OK** klicken können und die Arbeit an Objekten von nicht unterstützten Datenbankanbietern fortsetzen können, kann zur Laufzeit unerwartetes Verhalten auftreten.  
  
> [!NOTE]
>  Es werden nur Datenverbindungen unterstützt, die den .NET Framework\-Datenanbieter für SQL Server verwenden.  
  
### So beheben Sie diesen Fehler  
  
-   Klicken Sie auf **OK**, um mit dem Entwerfen der Entitätsklassen fortzufahren, die der Verbindung zugeordnet sind, die den nicht unterstützten Datenbankanbieter verwendet.Es kann unerwartetes Verhalten auftreten, wenn nicht unterstützte Datenbankanbieter verwendet werden.  
  
     \- oder \-  
  
-   Klicken Sie auf **Abbrechen**.  
  
     Die Aktion wird beendet.Erstellen oder verwenden Sie eine Datenverbindung, die .NET Framework\-Anbieter für SQL Server verwendet.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)