---
title: "Problembehandlung bei Ausnahmen: System.MissingMemberException | Microsoft Docs"
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
  - "MissingMemberException-Klasse"
ms.assetid: c4cf497b-0554-47fe-b2e9-81ee3eb9ec04
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.MissingMemberException
Eine <xref:System.MissingMemberException>\-Ausnahme wird ausgelöst, wenn versucht wird, dynamisch auf einen Klassenmember zuzugreifen, der nicht vorhanden ist.  
  
## Tipps  
 **Wenn ein Member in einer Klassenbibliothek entfernt oder umbenannt wurde, kompilieren Sie alle Assemblys erneut, die diese Bibliothek verwenden.**  
 Diese Ausnahme wird üblicherweise ausgelöst, wenn ein Feld oder eine Methode in einer Assembly gelöscht oder umbenannt wurde und diese Änderung in einer zweiten Assembly nicht vorgenommen wurde, die versucht, auf den fehlenden Member zuzugreifen.  
  
 **Wenn Sie auf Member einer spät gebundenen Objektvariable zugreifen, müssen Sie sicherstellen, dass diese als Public deklariert ist.**  
 Die `Protected`\-Variable, die `Friend`\-Variable und die `Private`\-Variable können in Visual Basic nicht spät gebunden werden.  
  
## Siehe auch  
 <xref:System.MissingMemberException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)