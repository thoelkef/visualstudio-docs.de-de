---
title: "Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgef&#252;hrten Programms verwendet? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.background"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Vordergrundprogramme"
  - "Debuggen [Visual Studio], Beim Beobachten von Vordergrundprogrammen"
  - "Fokus, Debuggen beim Beobachten von Vordergrundprogrammen"
  - "Vordergrundprogramm-Debuggen"
  - "Remotedebuggen, Debuggen von Vordergrundprogrammen"
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgef&#252;hrten Programms verwendet?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Problembeschreibung  
 Es liegt ein Problem beim Zeichnen auf dem Bildschirm vor.  Um das Problem beobachten zu können, muss das Programm im Vordergrund bleiben; das bedeutet jedoch, dass kein Zugriff auf die Debuggerfenster möglich wäre.  Welche Möglichkeiten gibt es?  
  
## Lösung  
 Wenn Sie über einen zweiten Computer verfügen, können Sie das Remotedebuggen verwenden.  So können Sie das Zeichnen auf dem Bildschirm auf dem Remotecomputer beobachten und gleichzeitig den Debugger auf dem Host ausführen.  Weitere Informationen zum Remotedebuggen finden Sie unter [Einrichten des Remotedebuggens](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)