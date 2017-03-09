---
title: "Die Klasse &quot;&lt;Klassenname&gt;&quot; muss eine &quot;Sub New&quot; deklarieren, da &quot;&lt;Konstruktorname&gt;&quot; in der &quot;&lt;Basisklassenname&gt;&quot;-Basisklasse als veraltet markiert ist | Microsoft Docs"
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
  - "vbc30917"
  - "bc30917"
helpviewer_keywords: 
  - "BC30917"
ms.assetid: 764d222d-e058-40ad-a354-29b956a8027b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Klasse &quot;&lt;Klassenname&gt;&quot; muss eine &quot;Sub New&quot; deklarieren, da &quot;&lt;Konstruktorname&gt;&quot; in der &quot;&lt;Basisklassenname&gt;&quot;-Basisklasse als veraltet markiert ist
Eine Klassendeklaration enthält keinen Konstruktor, und der Basisklassenkonstruktor ist mit dem Attribut <xref:System.ObsoleteAttribute> und der Direktive versehen, dies als Fehler zu behandeln.  
  
 Wenn eine abgeleitete Klasse keinen Konstruktor deklariert, versucht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] einen impliziten parameterlosen Konstruktor zu generieren, der `MyBase.New()` aufruft. Wenn kein zugänglicher Konstruktor in der Basisklasse vorhanden ist, der ohne Argumente aufgerufen werden kann, kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen impliziten Konstruktor generieren. In diesem Fall wird der erforderliche Konstruktor mit dem Attribut <xref:System.ObsoleteAttribute> markiert, damit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn nicht aufrufen kann.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 **Fehler\-ID:** BC30917  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie `Sub New`, um in der abgeleiteten Klasse einen Konstruktor zu deklarieren.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)