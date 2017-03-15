---
title: "Gemischter Code und fehlende Daten im Fenster &quot;Aufrufliste&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Verwalteter Code, Ausführen in Einzelschritten"
  - "Aufruflistenfenster, Debuggen im gemischten Modus"
  - "Aufruflistenfenster, Problembehandlung"
  - "Systemeigene Rahmen"
  - "Verwaltete Aufruflisten"
  - "Debuggen im gemischten Modus, Aufrufliste"
  - "Ausführen in Einzelschritten, aus verwaltetem Code heraus"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Gemischter Code und fehlende Daten im Fenster &quot;Aufrufliste&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Da es zwischen den Aufruflisten von verwaltetem Code und systemeigenen Code Unterschiede gibt, kann der Debugger bei vermischten Codetypen nicht immer die vollständige Aufrufliste anzeigen.  Wenn verwalteter Code durch systemeigenen Code aufgerufen wird, sind im Fenster **Aufrufliste** unter Umständen folgende Abweichungen festzustellen:  
  
-   Es kann vorkommen, dass der systemeigene Rahmen direkt über dem verwalteten Code im Fenster **Aufrufliste** fehlt.  Weitere Informationen finden Sie unter [Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Für außerhalb des Debuggers gestartete Anwendungen mit gemischtem Code wird im Fenster **Aufrufliste** unter Umständen keiner der systemeigenen Rahmen, sondern nur der verwaltete Code angezeigt.  
  
 Beide Fälle treten relativ selten ein.  In den meisten Fällen, in denen verwalteter Code durch systemeigenen Code aufgerufen wird, werden die Aufruflisten richtig angezeigt.  
  
## Siehe auch  
 [Gewusst wie: Verwenden des Fensters Aufrufliste](../debugger/how-to-use-the-call-stack-window.md)