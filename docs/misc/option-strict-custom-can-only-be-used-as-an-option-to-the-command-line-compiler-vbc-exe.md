---
title: "&#39;Option Strict Custom&#39; kann nur als Option f&#252;r den Befehlszeilencompiler (vbc.exe) verwendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Option Strict Custom&#39; kann nur als Option f&#252;r den Befehlszeilencompiler (vbc.exe) verwendet werden.
Die `Option Strict`\-Anweisung übernimmt nur `On` und `Off` als Argumente. `Option Strict Custom` ist nicht zulässig.  
  
 Verwenden Sie die `/optionstrict:custom`\-Compileroption, um eine Warnung auszugeben, wenn die strenge Sprachsemantik nicht beachtet wird.  
  
 **Fehler\-ID:** BC31141  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie `Option Strict Custom` aus dem Quellcode.  
  
2.  Geben Sie die `/optionstrict:custom`\-Option an. Weitere Informationen finden Sie unter [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
## Siehe auch  
 [Option \<keyword\> Statement](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)