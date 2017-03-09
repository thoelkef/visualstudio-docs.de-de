---
title: "Problembehandlung bei Ausnahmen: System.Data.SqlServerCe.SqlCeException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Data.SqlServerCe.SqlCeException-Ausnahme"
  - "SqlCeException-Ausnahme"
  - "SqlServerCe.SqlCeException-Ausnahme"
ms.assetid: b0414ab9-94f1-48cc-a2ee-763c005150d5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.SqlServerCe.SqlCeException
Eine `System.Data.SqlServerCe.SqlCeException`\-Ausnahme wird ausgelöst, wenn der zugrunde liegende Anbieter eine Warnung oder einen Fehler aus einer SQL Server Compact\-Datenquelle zurückgibt. Weitere Informationen zur Ursache dieses Fehlers finden Sie unter [Fehler bei SQL Server Compact](http://msdn2.microsoft.com/library/ms171849.aspx) auf der MSDN\-Website.  
  
## Hinweise  
 Eine `System.Data.SqlServerCe.SqlCeException` enthält immer mindestens eine Instanz von `System.Data.SqlServerCe.SqlCeError`. Die Klasse kann nicht geerbt werden.  
  
 Weitere Informationen finden Sie in der Dokumentation zur [SQL Server Compact 3.5\-Klassenbibliothek](http://go.microsoft.com/fwlink/?LinkID=102595).  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)