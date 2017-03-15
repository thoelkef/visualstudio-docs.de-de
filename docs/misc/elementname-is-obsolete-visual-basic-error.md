---
title: "&#39;&lt;Elementname&gt;&#39; ist veraltet (Visual Basic-Fehler) | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31075"
  - "bc31075"
helpviewer_keywords: 
  - "BC31075"
ms.assetid: 614d36a1-2fba-4d03-963c-1565e88b08a6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Elementname&gt;&#39; ist veraltet (Visual Basic-Fehler)
Eine Anweisung versucht, auf ein Programmierelement zuzugreifen, das mit dem <xref:System.ObsoleteAttribute>\-Attribut und der Direktive gekennzeichnet wurde, den Zugriffsversuch als Fehler zu behandeln.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 **Fehler\-ID:** BC31075  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass der Elementname im Quellcodeverweis richtig geschrieben ist.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)