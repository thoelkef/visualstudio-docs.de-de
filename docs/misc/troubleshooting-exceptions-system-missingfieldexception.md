---
title: "Problembehandlung bei Ausnahmen: System.MissingFieldException | Microsoft Docs"
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
  - "MissingFieldException-Klasse"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.MissingFieldException
Die <xref:System.MissingFieldException> wird bei dem Versuch ausgelöst, dynamisch auf ein nicht vorhandenes Feld zuzugreifen.  
  
## Tipps  
 **Wenn ein Feld in einer Klassenbibliothek entfernt oder umbenannt wurde, kompilieren Sie alle Assemblys erneut, die diese Bibliothek verwenden.**  
 Die Ausnahme wird normalerweise bei dem Versuch ausgelöst, dynamisch auf ein gelöschtes oder umbenanntes Feld einer Assembly zuzugreifen, auf das nicht mit seinem starken Namen verwiesen wird.  
  
## Siehe auch  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)