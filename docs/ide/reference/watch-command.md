---
title: "Befehl &quot;&#220;berwachung&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch-Befehl"
  - "Überwachung (Befehl)"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;&#220;berwachung&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt und öffnet eine angegebene Instanz eines **Überwachungsfensters**.  Mithilfe eines **Überwachungsfensters** können Sie die Werte von Variablen, Ausdrücken und Registern berechnen, um diese Werte zu bearbeiten und die Ergebnisse zu speichern.  
  
## Syntax  
  
```  
Debug.Watch[index]  
```  
  
## Argumente  
 `index`  
 Erforderlich.  Die Instanznummer des Überwachungsfensters.  
  
## Hinweise  
 `index` muss eine ganze Zahl sein.  Gültige Werte sind 1, 2, 3 oder 4.  
  
## Beispiel  
  
```  
>Debug.Watch1  
```  
  
## Siehe auch  
 [Fenster „Auto“ und „Lokal“](../../debugger/autos-and-locals-windows.md)   
 [Gewusst wie: Bearbeiten eines Werts in einem Variablenfenster](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Gewusst wie: Verwenden des Dialogfelds Schnellüberwachung](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)