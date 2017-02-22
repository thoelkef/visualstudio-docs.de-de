---
title: "Gewusst wie: Wechseln zu einem anderen Thread w&#228;hrend des Debuggings | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "Threads, Wechsel [Debuggen]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Wechseln zu einem anderen Thread w&#228;hrend des Debuggings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Debuggen einer Multithreadanwendung können Sie verschiedene Methoden verwenden, um vom Kontext des bearbeiteten Threads zu einem anderen Thread zu wechseln.  
  
### So wechseln Sie zu einem Thread, der im Fenster Threads angezeigt wird  
  
-   Doppelklicken Sie auf den Thread.  
  
### So wechseln Sie zu einem Thread in einem Quellcodefenster  
  
-   Klicken Sie im linken Bundsteg mit der rechten Maustaste auf einen Threadindikator, zeigen Sie auf **Wechseln zu**, und klicken Sie dann auf den Namen des Threads, zu dem gewechselt werden soll.  Im Kontextmenü werden nur die Threads an dieser bestimmten Position angezeigt.  
  
     Wenn keine Indikatoren angezeigt werden, klicken Sie mit der rechten Maustaste in das Fenster **Threads**, und überprüfen Sie, ob **Threads in Quelle anzeigen** ausgewählt ist.  
  
### So wechseln Sie über die Symbolleiste Debugspeicherort zu einem Thread  
  
1.  Klicken Sie auf der Symbolleiste **Debugspeicherort** auf das Feld **Thread**.  
  
2.  Klicken Sie in der Liste auf den Thread, zu dem Sie wechseln möchten.  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)