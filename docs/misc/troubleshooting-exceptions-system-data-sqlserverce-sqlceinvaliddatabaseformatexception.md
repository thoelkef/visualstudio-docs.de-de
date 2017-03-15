---
title: "Problembehandlung bei Ausnahmen: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SqlCeInvalidDatabaseFormatException-Ausnahme"
  - "System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException-Ausnahme"
ms.assetid: f5ca1f40-4619-4523-807e-d5b20bfb05b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException
Eine `System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException`\-Ausnahme tritt auf, wenn von SQL Server Compact eine Datenbankdatei geöffnet wird, die mit einer früheren Version des Produkts erstellt wurde.  
  
## Hinweise  
 Sie können die Datenbankdatei mit [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] oder mit der `System.Data.SqlServerCe.SqlCeEngine.Upgrade`\-API aktualisieren.  
  
 Weitere Informationen finden Sie in der Dokumentation zur [SQL Server Compact 3.5\-Klassenbibliothek](http://go.microsoft.com/fwlink/?LinkID=102595).  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)