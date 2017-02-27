---
title: "Befehl &quot;Gehe zu&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto-Befehl"
  - "Gehe zu (Befehl)"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Befehl &quot;Gehe zu&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bewegt den Cursor in die angegebene Zeile.  
  
## Syntax  
  
```  
Edit.GoTo [linenumber]  
```  
  
## Argumente  
 `linenumber`  
 Optional.  Eine ganze Zahl, die die Zahl der Zeile angibt, in die der Cursor bewegt werden soll.  
  
## Hinweise  
 Die Zeilennummerierung beginnt bei 1.  Wenn der Wert von `linenumber` kleiner als 1 ist, wird die erste Zeile angezeigt.  Wenn der Wert von `linenumber` größer als die Nummer der letzten Zeile ist, wird die letzte Zeile angezeigt.  
  
 Wenn kein Wert für `linenumber` angegeben ist, wird das Dialogfeld **Gehe zu Zeile** angezeigt.  
  
 Der Alias für diesen Befehl lautet **GoToLn**.  
  
## Beispiel  
  
```  
>Edit.GoTo 125  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)