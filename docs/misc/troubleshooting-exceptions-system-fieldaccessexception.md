---
title: "Problembehandlung bei Ausnahmen: System.FieldAccessException | Microsoft Docs"
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
  - "FieldAccessException-Klasse"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.FieldAccessException
Eine <xref:System.FieldAccessException>\-Ausnahme wird bei dem Versuch ausgelöst, auf ein privates oder geschütztes Feld innerhalb einer Klasse zuzugreifen.  
  
## Tipps  
 **Wenn die Feldzugriffsebene in einer Klassenbibliothek geändert wurde, müssen Sie alle Assemblys mit Verweisen auf diese Bibliothek neu kompilieren.**  
 Die Ausnahme wird in der Regel dann ausgelöst, wenn die Zugriffsebene \(`Public`, `Private` usw.\) eines Felds geändert wird und Assemblys mit einem Verweis auf die Bibliothek nicht neu kompiliert werden.  
  
## Siehe auch  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)