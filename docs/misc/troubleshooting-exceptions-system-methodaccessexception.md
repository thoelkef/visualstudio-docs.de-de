---
title: "Problembehandlung bei Ausnahmen: System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException-Klasse"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.MethodAccessException
<xref:System.MethodAccessException> wird bei einem ungültigen Versuch ausgelöst, auf eine private oder geschützte Methode innerhalb einer Klasse zuzugreifen.  
  
## Tipps  
 **Wenn sich die Zugriffsebene einer Methode in einer Klassenbibliothek geändert hat, kompilieren Sie alle auf die Bibliothek verweisenden Assemblys neu.**  
 Diese Ausnahme tritt in der Regel auf, wenn der Aufrufer keine Zugriffsberechtigung für den Member hat.  
  
## Siehe auch  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)