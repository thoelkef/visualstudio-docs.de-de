---
title: "Befehl &quot;Wurzel setzen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix-Befehl"
  - "Basis festlegen (Befehl)"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;Wurzel setzen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt die numerische Basis zum Anzeigen ganzzahliger Werte fest bzw. gibt diese zurück.  
  
## Syntax  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## Argumente  
 `10` oder `16` oder `hex` oder `dec`  
 Optional.  Gibt eine dezimale \(10 oder dec\) oder hexadezimale \(16 oder hex\) Notation an.  Wenn ein Argument ausgelassen wird, wird der Wert der aktuellen Basis zurückgegeben.  
  
## Beispiel  
 In diesem Beispiel wird die Umgebung festgelegt, um ganzzahlige Werte im Hexadezimalformat anzuzeigen.  
  
```  
>Debug.SetRadix hex  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)