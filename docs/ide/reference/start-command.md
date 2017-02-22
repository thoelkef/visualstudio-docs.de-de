---
title: "Befehl &quot;Start&quot; | Microsoft Docs"
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
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start-Befehl"
  - "Start (Befehl)"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Start&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Startet das Debuggen des Startprojekts.  
  
## Syntax  
  
```  
Debug.Start [address]  
```  
  
## Argumente  
 `address`  
 Optional.  Adresse, an der die Ausführung des Programms unterbrochen wird, ähnlich einem Haltepunkt in Quellcode.  Dieses Argument ist nur im Debugmodus gültig.  
  
## Hinweise  
 Der **Start**\-Befehl führt bei der Ausführung einen RunToCursor\-Vorgang bis zur angegebenen Adresse aus.  
  
## Beispiel  
 In diesem Beispiel wird der Debugger gestartet, wobei alle dabei auftretenden Ausnahmen ignoriert werden.  
  
```  
>Debug.Start  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)