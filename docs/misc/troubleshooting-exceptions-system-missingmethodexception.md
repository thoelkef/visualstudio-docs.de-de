---
title: "Problembehandlung bei Ausnahmen: System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "MissingMethodException-Klasse"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.MissingMethodException
Eine <xref:System.MissingMethodException>\-Ausnahme wird bei dem Versuch ausgelöst, dynamisch auf eine nicht vorhandene Methode zuzugreifen.  
  
## Tipps  
 **Wenn eine Methode in einer Klassenbibliothek entfernt oder umbenannt wurde, kompilieren Sie alle auf diese Methode verweisenden Assemblys erneut.**  
 Diese Ausnahme wird normalerweise bei dem Versuch ausgelöst, dynamisch auf eine gelöschte oder umbenannte Methode einer Assembly zuzugreifen, auf die nicht mit ihrem starken Namen verwiesen wird.  
  
## Hinweise  
 Beim Aufrufen einer nicht verwalteten Funktion wird diese Ausnahme ausgelöst, wenn die CLR das Modul oder die Funktion nicht finden kann.  
  
## Siehe auch  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)