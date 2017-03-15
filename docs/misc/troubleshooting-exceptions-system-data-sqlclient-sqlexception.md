---
title: "Problembehandlung bei Ausnahmen: System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "SqlException-Klasse"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.SqlClient.SqlException
Eine <xref:System.Data.SqlClient.SqlException>\-Ausnahme wird generiert, wenn von SQL Server eine Warnung oder ein Fehler zurückgegeben wird.  
  
## Tipps  
 **Stellen Sie sicher, dass Sie gültige Anmeldeinformationen verwenden.**  
 Stellen Sie sicher, dass die von Ihnen angegebenen Anmeldeinformationen gültig sind. Weitere Informationen finden Sie unter [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md).  
  
 **Stellen Sie sicher, dass der Servername korrekt ist und der Server läuft.**  
 Stellen Sie sicher, dass Sie den korrekten Servernamen verwenden und dass der Server erreichbar ist.  
  
### Hinweise  
 Diese Ausnahme wird jedes Mal ausgelöst, wenn der .NET Framework\-Datenanbieter für SQL Server auf einen vom Server generierten Fehler trifft.  
  
 Meldungen mit einem Schweregrad von 10 oder darunter dienen rein der Information. Sie zeigen Probleme an, die durch fehlerhafte Benutzereingaben verursacht wurden. Schweregrade von 11 bis 16 werden vom Benutzer generiert und können vom Benutzer korrigiert werden. Schweregrade von 17 bis 25 zeigen Software\- oder Hardwarefehler an. Bei einem Fehler mit Schweregrad 17, 18 oder 19 können Sie mit der Arbeit fortfahren, auch wenn Sie eine bestimmte Anweisung möglicherweise nicht mehr ausführen können.  
  
 Die <xref:System.Data.SqlClient.SqlConnection> bleibt hergestellt, wenn der Schweregrad 19 oder darunter beträgt. Wenn der Schweregrad 20 oder größer ist, schließt der Server normalerweise die <xref:System.Data.SqlClient.SqlConnection>\-Klasse. Die Benutzer können die Verbindung aber erneut öffnen und fortfahren. In beiden Fällen wird von der Methode, die den Befehl ausführt, eine <xref:System.Data.SqlClient.SqlException> generiert.  
  
 Weitere Informationen über Warnungen und sonstige Meldungen, die von SQL Server gesendet werden, finden Sie im Abschnitt Problembehandlung der SQL Server\-Onlinedokumentation.  
  
## Siehe auch  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)