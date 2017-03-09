---
title: "Problembehandlung bei Ausnahmen: System.Data.Odbc.OdbcException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHOdbc"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Ausnahmen, ODBC"
  - "ODBC, Ausnahmen"
  - "OdbcException-Klasse"
ms.assetid: 5f2c2167-cf7b-4634-af86-44dc71eff02d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.Odbc.OdbcException
Eine <xref:System.Data.Odbc.OdbcException>\-Ausnahme wird ausgelöst, wenn eine Warnung oder ein Fehler von einer ODBC\-Datenquelle zurückgegeben wird.  
  
## Tipps  
 **Stellen Sie sicher, dass Sie gültige Anmeldeinformationen verwenden.**  
 Überprüfen Sie, ob die Anmeldeinformationen gültig sind.  
  
 **Stellen Sie sicher, dass der Servername korrekt ist und der Server läuft.**  
 Stellen Sie sicher, dass Sie den korrekten Servernamen verwenden und dass der Server erreichbar ist.  
  
## Hinweise  
 Diese Ausnahme wird immer dann ausgelöst, wenn der <xref:System.Data.Odbc.OdbcDataAdapter> auf einen vom Server generierten Fehler trifft.  
  
 Wenn die Auswirkungen des Fehlers zu schwerwiegend sind, trennt der Server möglicherweise die <xref:System.Data.Odbc.OdbcConnection>. Die Benutzer können die Verbindung aber erneut öffnen und fortfahren.  
  
## Siehe auch  
 <xref:System.Data.Odbc.OdbcException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)