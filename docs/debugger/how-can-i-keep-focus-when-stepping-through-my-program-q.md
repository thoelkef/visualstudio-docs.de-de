---
title: "Wie kann der Fokus beim Durchlaufen des Programms beibehalten werden? | Microsoft Docs"
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
  - "vs.debug.stepping"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [C++], Ausführen in Einzelschritten"
  - "Fokus, Beibehalten"
  - "Ausführen in Einzelschritten, Fokus"
  - "Fenster, Aktivierung der Problembehandlung"
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie kann der Fokus beim Durchlaufen des Programms beibehalten werden?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Beschreibung  
 Das Programm hat Probleme mit der Aktivierung von Fenstern.  Beim Durchlaufen des Programms mit dem Debugger kann das Problem nicht reproduziert werden, da das Programm den Fokus verliert.  Wie kann dies vermieden werden?  
  
## Lösung  
 Wenn Sie über einen zweiten Computer verfügen, verwenden Sie das Remotedebuggen.  Sie können das Programm auf dem Remotecomputer verwenden, während der Debugger auf dem Host ausgeführt wird.  Weitere Informationen finden Sie unter [How to: Select a Remote Computer](http://msdn.microsoft.com/de-de/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)