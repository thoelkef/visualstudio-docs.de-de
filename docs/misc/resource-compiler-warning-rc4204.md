---
title: "Ressourcencompiler: Warnung RC4204 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Ressourcencompiler: Warnung RC4204
ASCII\-Zeichen entspricht nicht dem virtuellem Tastencode  
  
 Für den virtueller Tastencode in einer VIRTKEY\-Zugriffstaste wurde ein Zeichenfolgenliteral verwendet.  
  
 Trotz der Warnung können Sie den Vorgang fortsetzen. Sie informiert Sie jedoch darüber, dass die generierten Zugriffstasten möglicherweise nicht mit der Zeichenfolge übereinstimmen, die Sie angegeben haben. \(VIRTKEY\-Zugriffstasten verwenden andere Tastencodes als ASCII\-Zugriffstasten.\)  
  
 Obwohl Zeichenfolgenliterale syntaktisch zulässig sind, können Sie nur sicherstellen, dass Sie die gewünschte Zugriffstaste erhalten, indem Sie die **VK\_\*** `#define`\-Werte in „WINDOWS.h“ verwenden.