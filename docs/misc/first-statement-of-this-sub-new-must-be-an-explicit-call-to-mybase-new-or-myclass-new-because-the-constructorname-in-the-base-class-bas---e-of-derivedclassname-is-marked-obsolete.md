---
title: "Die erste Anweisung dieses &quot;Sub New&quot; muss ein expliziter Aufruf von &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein, da der Konstruktor&quot;&lt;Konstruktorname&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; von &quot;&lt;Name der abgeleiteten Klasse&gt;&quot; als veraltet markiert ist. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die erste Anweisung dieses &quot;Sub New&quot; muss ein expliziter Aufruf von &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein, da der Konstruktor&quot;&lt;Konstruktorname&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; von &quot;&lt;Name der abgeleiteten Klasse&gt;&quot; als veraltet markiert ist.
Ein Klassenkonstruktor ruft nicht explizit einen Basisklassenkonstruktor auf, und der implizite Basisklassenkonstruktor ist mit dem Attribut <xref:System.ObsoleteAttribute> und der Direktive versehen, dies als Fehler zu behandeln.  
  
 Wenn der Konstruktor einer abgeleiteten Klasse keinen Basisklassenkonstruktor aufruft, versucht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], einen impliziten Aufruf eines parameterlosen Basisklassenkonstruktors zu generieren. Wenn kein zugänglicher Konstruktor in der Basisklasse vorhanden ist, der ohne Argumente aufgerufen werden kann, kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen impliziten Aufruf generieren. In diesem Fall wird der erforderliche Konstruktor mit dem Attribut <xref:System.ObsoleteAttribute> markiert, damit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn nicht aufrufen kann.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die Eigenschaft <xref:System.ObsoleteAttribute.IsError%2A> des Attributs entweder auf `True` oder `False` einstellen. Wenn Sie die Einstellung `True` vornehmen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie die Einstellung `False` vornehmen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 **Fehler\-ID:** BC30919  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie einen Aufruf von `MyBase.New()` oder `MyClass.New()` als erste Anweisung von `Sub New` in der abgeleiteten Klasse ein.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)