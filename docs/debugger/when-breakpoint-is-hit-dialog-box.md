---
title: "Dialogfeld &quot;Beim Erreichen eines Haltepunktes&quot; | Microsoft Docs"
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
  - "vs.debug.whenbreakpointishit"
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
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dialogfeld &quot;Beim Erreichen eines Haltepunktes&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Aktion anpassen, die beim Erreichen eines Haltepunkts ausgeführt wird.  
  
## UIElement-Liste  
 **Meldung drucken**  
 Druckt eine Meldung mithilfe der DebuggerDisplay\-Syntax.  Weitere Informationen finden Sie unter [Verwenden des DebuggerDisplay\-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Dieses Textfeld unterstützt auch spezielle Schlüsselwörter \(z. B. $ADDRESS\), die alleine oder innerhalb der geschweiften Klammern eines DebuggerDisplay\-Ausdrucks verwendet werden können.  Die verfügbaren Schlüsselwörter werden im Dialogfeld aufgelistet.  
  
 **Ausführung fortsetzen**  
 Dieses Steuerelement ist nur aktiviert, wenn **Meldung drucken** ausgewählt ist.  Durch Auswählen dieses Steuerelements können Sie einen Haltepunkt als Ablaufverfolgungspunkt verwenden, um die Programmausführung zu verfolgen, statt beim Erreichen des Haltepunkts zu unterbrechen.  
  
## Siehe auch  
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)   
 [Verwenden des DebuggerDisplay\-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)