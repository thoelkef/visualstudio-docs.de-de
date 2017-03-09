---
title: "Fehler beim Einbetten des Win32-Manifests: Die Option &#39;/win32manifest&#39; verursacht Konflikte mit &#39;/nowin32manifest&#39;. | Microsoft Docs"
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
  - "vbc2033"
  - "bc2033"
helpviewer_keywords: 
  - "BC2033"
ms.assetid: e921b34a-1ab3-4ba0-81b3-e45c62de4718
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler beim Einbetten des Win32-Manifests: Die Option &#39;/win32manifest&#39; verursacht Konflikte mit &#39;/nowin32manifest&#39;.
Dem Visual Basic\-Compiler wurde sowohl die `/win32manifest`\- als auch die `/nowin32manifest`\-Compileroption übergeben. Nur eine dieser Optionen kann an den Visual Basic\-Compiler übergeben werden.  
  
 **Fehler\-ID:** BC2033  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie entweder die Compileroption `/win32manifest` oder `/nowin32manifest`.  
  
## Siehe auch  
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [\/nowin32manifest](/dotnet/visual-basic/reference/command-line-compiler/nowin32manifest)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)