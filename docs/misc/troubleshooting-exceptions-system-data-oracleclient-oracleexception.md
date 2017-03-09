---
title: "Problembehandlung bei Ausnahmen: System.Data.OracleClient.OracleException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OracleException-Klasse"
  - "Oracle"
  - "Ausnahmen, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.OracleClient.OracleException
Eine <xref:System.Data.OracleClient.OracleException>\-Ausnahme wird generiert, wenn von der Oracle\-Datenbank oder dem .NET Framework\-Datenanbieter für Oracle eine Warnung oder ein Fehler zurückgegeben wird.  
  
## Tipps  
 **Stellen Sie sicher, dass Sie gültige Anmeldeinformationen verwenden.**  
 Stellen Sie sicher, dass die von Ihnen angegebenen Anmeldeinformationen gültig sind.  
  
 **Stellen Sie sicher, dass der Servername korrekt ist und der Server läuft.**  
 Stellen Sie sicher, dass Sie den korrekten Servernamen verwenden und dass der Server erreichbar ist.  
  
## Hinweise  
 Diese Ausnahme wird immer dann ausgelöst, wenn der <xref:System.Data.OracleClient.OracleDataAdapter> auf einen vom Server generierten Fehler trifft.  
  
 Wenn die Auswirkungen des Fehlers zu schwerwiegend sind, trennt der Server möglicherweise die <xref:System.Data.OracleClient.OracleConnection>. Die Benutzer können die Verbindung aber erneut öffnen und fortfahren.  
  
## Siehe auch  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)