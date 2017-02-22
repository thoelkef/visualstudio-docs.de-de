---
title: "Aktuellen Prozess festlegen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess-Befehl"
  - "Aktuellen Prozess festlegen (Befehl)"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Aktuellen Prozess festlegen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt den angegebenen Prozess als aktiven Prozess im Debugger fest.  
  
## Syntax  
  
```  
Debug.SetCurrentProcess index  
```  
  
## Argumente  
 `index`  
 Erforderlich.  Der Index des Prozesses.  
  
## Hinweise  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv.  Zum Festlegen des aktiven Prozesses können Sie den Befehl `SetCurrentProcess` verwenden.  
  
## Beispiel  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)