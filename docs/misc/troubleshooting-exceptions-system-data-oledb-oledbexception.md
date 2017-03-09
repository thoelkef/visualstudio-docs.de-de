---
title: "Problembehandlung bei Ausnahmen: System.Data.OleDb.OleDbException | Microsoft Docs"
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
  - "OLEDB"
  - "OleDbException-Klasse"
  - "Ausnahmen, OLEDB"
ms.assetid: f50077cf-e411-41f0-b73e-19eef83036c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.OleDb.OleDbException
Eine <xref:System.Data.OleDb.OleDbException>\-Ausnahme wird generiert, wenn eine OLE DB\-Datenquelle eine Warnung oder einen Fehler zurückgibt.  
  
## Tipps  
 **Stellen Sie sicher, dass Sie gültige Anmeldeinformationen verwenden.**  
 Stellen Sie sicher, dass die von Ihnen angegebenen Anmeldeinformationen gültig sind. Weitere Informationen finden Sie unter <xref:System.Data.OleDb.OleDbErrorCollection>.  
  
 **Stellen Sie sicher, dass der Servername korrekt ist und der Server läuft.**  
 Stellen Sie sicher, dass Sie den korrekten Servernamen verwenden und dass der Server erreichbar ist. Weitere Informationen finden Sie unter <xref:System.Data.OleDb.OleDbErrorCollection>.  
  
### Hinweise  
 Diese Ausnahme wird jedes Mal ausgelöst, wenn der .NET Framework\-Datenanbieter für OLE DB auf einen vom Server generierten Fehler trifft.  
  
 Wenn die Auswirkungen des Fehlers zu schwerwiegend sind, trennt der Server möglicherweise die <xref:System.Data.OleDb.OleDbConnection>. Die Benutzer können die Verbindung aber erneut öffnen und fortfahren.  
  
## Siehe auch  
 <xref:System.Data.OleDb.OleDbException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)