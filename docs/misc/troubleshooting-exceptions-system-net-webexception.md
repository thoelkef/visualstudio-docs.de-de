---
title: "Problembehandlung bei Ausnahmen: System.Net.WebException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "WebException-Klasse"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Net.WebException
Eine <xref:System.Net.WebException>\-Ausnahme wird ausgelöst, wenn beim Zugriff auf das Netzwerk über ein austauschbares Protokoll ein Fehler auftritt.  
  
## Tipps  
 **Überprüfen Sie die Response\-Eigenschaft der Ausnahme, um zu bestimmen, warum die Anforderung nicht ausgeführt werden konnte.**  
 Wenn eine <xref:System.Net.WebException>\-Ausnahme durch eine Ableitung der <xref:System.Net.WebRequest>\-Klasse ausgelöst wird, stellt die <xref:System.Net.WebException.Response%2A>\-Eigenschaft die Internetantwort für die Anwendung bereit.  
  
 **Überprüfen Sie die Status\-Eigenschaft, um zu bestimmen, warum die Anforderung nicht ausgeführt werden konnte.**  
 Die <xref:System.Net.WebException.Status%2A>\-Eigenschaft der Ausnahme enthält Statusinformationen für den Fehler. Weitere Informationen finden Sie unter <xref:System.Net.WebExceptionStatus>.  
  
 **Wenn Sie bei der schrittweisen Ausführung eines XML\-Webdiensts das Zeitlimit überschreiten, legen Sie den Timeoutwert für den XML\-Webdienstaufruf auf unendlich fest.**  
 Weitere Informationen finden Sie unter [Fehler: Timeout während des Debuggens von Webdiensten](../debugger/error-timeout-while-debugging-web-services.md).  
  
## Siehe auch  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Gewusst wie: Senden von Daten mithilfe der WebRequest\-Klasse](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Gewusst wie: Anfordern von Daten mithilfe der WebRequest\-Klasse](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Gewusst wie: Abrufen eines protokollspezifischen WebResponse, das einem WebRequest entspricht](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)