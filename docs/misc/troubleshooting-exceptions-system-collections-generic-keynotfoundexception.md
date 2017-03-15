---
title: "Problembehandlung bei Ausnahmen: System.Collections.Generic.KeyNotFoundException | Microsoft Docs"
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
  - "KeyNotFoundException-Klasse"
ms.assetid: de33f5bb-5709-46fe-b889-7105dbd24299
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Collections.Generic.KeyNotFoundException
Eine <xref:System.Collections.Generic.KeyNotFoundException>\-Ausnahme wird ausgelöst, wenn versucht wird, mit einem nicht existierenden Schlüssel einen Schlüssel oder ein Schlüssel\/Wert\-Paar aus einer Auflistung abzufragen.  
  
## Tipps  
 **Stellen Sie sicher, dass der verwendete Schlüssel in der Auflistung vorhanden ist, auf die Sie zugreifen.**  
 Diese Ausnahme wird ausgelöst, wenn eine Operation versucht, ein Element aus einer Auflistung abzurufen und dabei einen Schlüssel verwendet, der in dieser Auflistung nicht vorhanden ist.  
  
### Hinweise  
 Mit der <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>\-Methode kann ermittelt werden, ob ein Schlüssel vorhanden ist.  
  
## Siehe auch  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.KeyNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)