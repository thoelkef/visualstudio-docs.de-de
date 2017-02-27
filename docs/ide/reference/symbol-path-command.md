---
title: "Befehl &quot;Symbolpfad&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath-Befehl"
  - "Symbolpfad (Befehl)"
  - "SymbolPath-Befehl"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Befehl &quot;Symbolpfad&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht.  
  
## Syntax  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## Argumente  
 `pathname`  
 Optional.  Ein durch Semikolons getrennte Liste der Pfade, in denen der Debugger nach Symbolen sucht.  
  
## Hinweise  
 Wenn kein `pathname` angegeben wird, werden von dem Befehl die aktuellen Symbolpfade aufgelistet.  
  
## Beispiel  
 In diesem Beispiel werden der Liste mit Symbolverzeichnissen zwei Pfade hinzugefügt.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## Beispiel  
 In diesem Beispiel wird eine durch Semikolons getrennte Liste der aktuellen Symbolpfade angezeigt.  
  
```  
Debug.SymbolPath  
```  
  
## Siehe auch  
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)