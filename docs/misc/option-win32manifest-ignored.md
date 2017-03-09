---
title: "Die Option /win32manifest wird ignoriert | Microsoft Docs"
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
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Option /win32manifest wird ignoriert
Die Option \/win32manifest wird ignoriert Sie kann nur angegeben werden, wenn das Ziel eine Assembly ist.  
  
 Dem Visual Basic\-Compiler wurde die `/win32manifest`\-Compileroption übergeben, als die `/target`\-Option auf `module` festgelegt ist.  
  
 **Fehler\-ID:** BC2034  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `/win32manifest`\-Compileroption, oder legen Sie die `/target`\-Option auf `exe`, `winexe` oder `library` fest.  
  
## Siehe auch  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)