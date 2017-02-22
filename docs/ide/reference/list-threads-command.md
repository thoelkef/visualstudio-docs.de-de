---
title: "Befehl &quot;Threads auflisten&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads-Befehl"
  - "Threads auflisten (Befehl)"
  - "ListThreads-Befehl"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Threads auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt eine Liste der Threads im aktuellen Programm an.  
  
## Syntax  
  
```  
Debug.ListThreads [index]  
```  
  
## Argumente  
 `index`  
 Optional.  Wählt einen Thread nach seinem Index als aktuellen Thread aus.  
  
## Hinweise  
 Wenn festgelegt, wird der angegebene Thread durch das `index`\-Argument als aktueller Thread gekennzeichnet.  Neben dem aktuellen Thread wird in der Liste ein Sternchen \(\*\) angezeigt.  
  
## Beispiel  
  
```  
>Debug.ListThreads   
```  
  
## Siehe auch  
 [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)   
 [Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)