---
title: "Fehler beim Einbetten des Win32-Manifests: &lt;manifest&gt;. | Microsoft Docs"
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
  - "vbc31191"
  - "bc31191"
helpviewer_keywords: 
  - "BC31191"
ms.assetid: 5babed58-d024-4acd-9838-fab8f07c4a37
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler beim Einbetten des Win32-Manifests: &lt;manifest&gt;.
Die für die Compileroption `/win32manifest` angegebene Datei darf nicht eingebettet sein. Dies kann die Folge unzureichender Sicherheitsberechtigungen für die Manifestdatei sein.  
  
 **Fehler\-ID:** BC31191  
  
### So beheben Sie diesen Fehler  
  
1.  Achten Sie darauf, dass die Identität, die den Visual Basic\-Compilerbefehl ausführt, Zugriff auf die Win32\-Manifestdatei hat.  
  
## Siehe auch  
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)