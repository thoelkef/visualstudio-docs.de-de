---
title: "Dialogfeld &quot;Der Wert kann nicht ge&#228;ndert werden&quot; | Microsoft Docs"
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
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Der Wert kann nicht geändert werden (Dialogfeld)"
  - "Variablen [Debugger], bearbeiten"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dialogfeld &quot;Der Wert kann nicht ge&#228;ndert werden&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Fehler  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 Dieses Meldungsfeld wird angezeigt, wenn Sie versuchen, den Inhalt einer Variablen im Debuggerfenster \(Fenster "Auto", "Überwachung" oder "Lokal"\) oder im Dialogfeld "Schnellüberwachung" auf einen ungültigen Wert zu ändern.  Diese Meldung wird beispielsweise angezeigt, wenn Sie versuchen, den Wert einer Variablen mit einer ganzen Zahl in eine Zeichenfolge zu ändern.  
  
## Lösung  
 Stellen Sie sicher, dass der Wert, den Sie im Debuggerfenster oder im Fenster "Schnellüberwachung"eingeben, ein zulässiger Wert für die festzulegende Variable ist.  
  
## Siehe auch  
 [Ausdrücke im Debugger](../debugger/expressions-in-the-debugger.md)