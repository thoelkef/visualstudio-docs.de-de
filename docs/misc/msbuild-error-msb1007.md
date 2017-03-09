---
title: "MSBuild Error MSB1007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingLoggerError"
helpviewer_keywords: 
  - "MSB1007"
ms.assetid: bf45dbc3-50cd-488a-87df-9e647cd71f10
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1007
**Geben Sie eine Protokollierung an.**  
  
 Eine Protokollierung muss für den Schalter **\/logger** angegeben werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie sowohl unter Verwendung der Protokollierungsklasse als auch der Protokollierungsassembly eine Protokollierung an.  Die `<logger>`\-Syntax lautet:  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     Die `<logger class>`\-Syntax lautet:  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     Die `<logger assembly>`\-Syntax lautet:  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` sind optional und werden so an die Protokollierung übergeben, wie sie eingegeben wurden.  
  
     Einige Beispiele für den Schalter **\/logger** lauten:  
  
     `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
     `/logger:XMLLogger,C:\Loggers\MyLogger.dll`  
  
     `/logger:XMLLogger,..  \Loggers\MyLogger.dll;OutputAsHTML`  
  
## Siehe auch  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)