---
title: "Befehl &quot;Aktuellen Wert anzeigen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch-Befehl"
  - "Schnellansicht (Befehl)"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;Aktuellen Wert anzeigen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt den ausgewählten oder angegebenen Text im Feld Ausdruck des [Dialogfelds Schnellüberwachung](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md) an.  In diesem Dialogfeld können Sie den aktuellen Wert der vom Debugger erkannten Variablen oder Ausdrücke oder den Inhalt eines Registers berechnen.  Darüber hinaus können Sie den Wert beliebiger, nicht konstanter Variablen oder den Inhalt eines beliebigen Registers ändern.  
  
## Syntax  
  
```  
Debug.QuickWatchq [text]  
```  
  
## Argumente  
 `text`  
 Optional.  Der Text, der dem Dialogfeld **Schnellüberwachung** hinzugefügt werden soll.  
  
## Hinweise  
 Wenn `text` ausgelassen wird, wird dem Überwachungsfenster der aktuell ausgewählte Text oder das ausgewählte Wort an der Cursorposition hinzugefügt.  
  
## Beispiel  
  
```  
>Debug.QuickWatch  
```  
  
## Siehe auch  
 [Gewusst wie: Verwenden des Dialogfelds Schnellüberwachung](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)