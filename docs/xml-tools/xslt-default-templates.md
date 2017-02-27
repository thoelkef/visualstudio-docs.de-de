---
title: "XSLT-Standardvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# XSLT-Standardvorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Standardvorlage wird bei der XSLT\-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist.Die Standardvorlage \(oder integrierte Vorlagenregel\) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert.Mithilfe der Standardvorlage kann der XSLT\-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde.Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL\-Transformation führen.  
  
 Der XSLT\-Debugger zeigt nun den Code von XSLT\-Standardvorlagen an.Bei den einzelnen Schritten einer XSL\-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an.Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.  
  
## Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)