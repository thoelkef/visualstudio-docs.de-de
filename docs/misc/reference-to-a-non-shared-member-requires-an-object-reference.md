---
title: "Der Verweis auf einen nicht freigegebenen Member erfordert einen Objektverweis | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Verweis auf einen nicht freigegebenen Member erfordert einen Objektverweis
Sie haben auf einen nicht freigegebenen Member im Code verwiesen, ohne einen Objektverweis bereitzustellen. Sie können nicht den Klassennamen selbst für die Qualifizierung eines nicht freigegebenen Members verwenden. Die Instanz muss zunächst als Objektvariable deklariert werden, auf die dann durch den Variablennamen verwiesen werden kann.  
  
 **Fehler\-ID:** BC30469  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren Sie die Instanz als Objektvariable.  
  
2.  Verweisen Sie über den Variablennamen auf die Instanz.  
  
## Siehe auch  
 [NICHT im BUILD: Grundlegendes zu Klassen](http://msdn.microsoft.com/de-de/cc2355a2-cb98-4353-9440-736585aec46c)   
 [NICHT IM BUILD: Freigegebene Member in Visual Basic](http://msdn.microsoft.com/de-de/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NICHT IM BUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9)