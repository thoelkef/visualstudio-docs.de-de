---
title: "Befehl &quot;Haltepunkt ein/aus&quot; | Microsoft Docs"
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
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint-Befehl"
  - "Haltepunkt umschalten (Befehl)"
  - "ToggleBreakpoint-Befehl"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Haltepunkt ein/aus&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Schaltet den Haltepunkt entweder ein oder aus, je nach seinem aktuellen Status an der aktuellen Position in der Datei.  
  
## Syntax  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## Argumente  
 `text`  
 Optional.  Wenn Text angegeben wird, wird die Zeile als benannter Haltepunkt markiert.  Andernfalls wird die Zeile als unbenannter Haltepunkt markiert; dieses Verhalten ist ähnlich dem, das durch Drücken von F9 ausgelöst wird.  
  
## Beispiel  
 Im folgenden Beispiel wird der aktuelle Haltepunkt umgeschaltet.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)