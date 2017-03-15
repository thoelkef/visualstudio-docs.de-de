---
title: "Problembehandlung bei Ausnahmen: System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException-Klasse"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Net.HttpListenerException
<xref:System.Net.HttpListenerException> wird ausgelöst, wenn ein Fehler bei der Verarbeitung einer Hypertext Transfer Protocol\-Anforderung auftritt.  
  
## Tipps  
 Achten Sie darauf, dass Sie nur URI\-Präfixe registrieren, die noch nicht registriert sind.  
 Wenn das URI\-Präfix bereits registriert ist, wird diese Ausnahme ausgelöst.  
  
 Stellen Sie sicher, dass die HTTP\-Anforderung gültig ist.  
 Die Ausnahme wird von der <xref:System.Net.HttpListener>\-Klasse und allen zugeordneten Klassen ausgelöst, wenn ein Fehler bei der Initialisierung von <xref:System.Net.HttpListener> oder beim Erstellen oder Senden einer Antwort auf eine HTTP\-Aufforderung auftritt.  
  
 Wenn Sie die `HttpListenerPrefixCollection.Add`\-Methode verwenden, müssen Sie sicherstellen, dass `uriPrefix` nicht bereits hinzugefügt wurde.  
 Diese Ausnahme wird ausgelöst, wenn bereits ein anderer <xref:System.Net.HttpListener> das `uriPrefix`\-Präfix hinzugefügt hat.  
  
## Siehe auch  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)