---
title: "Die erste Anweisung dieser &quot;Sub New&quot; muss ein expliziter Aufruf von &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein, da der &quot;&lt;Konstruktorname&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; von &quot;&lt;Name der abgeleiteten Klasse&gt;&quot; als veraltet markiert ist. | Microsoft Docs"
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
  - "bc41003"
  - "vbc41003"
helpviewer_keywords: 
  - "BC41003"
ms.assetid: 6d7c84db-659f-4388-85cf-38208ad607c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die erste Anweisung dieser &quot;Sub New&quot; muss ein expliziter Aufruf von &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein, da der &quot;&lt;Konstruktorname&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; von &quot;&lt;Name der abgeleiteten Klasse&gt;&quot; als veraltet markiert ist.
Ein Klassenkonstruktor ruft nicht explizit einen Basisklassenkonstruktor auf, und der implizite Basisklassenkonstruktor ist mit dem <xref:System.ObsoleteAttribute>\-Attribut und der Direktive versehen, dies als Warnung zu behandeln.  
  
 Wenn der Konstruktor einer abgeleiteten Klasse keinen Basisklassenkonstruktor aufruft, versucht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], einen impliziten Aufruf eines parameterlosen Basisklassenkonstruktors zu generieren. Wenn kein zugänglicher Konstruktor in der Basisklasse vorhanden ist, der ohne Argumente aufgerufen werden kann, kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen impliziten Aufruf generieren. In diesem Fall wird der erforderliche Konstruktor mit dem <xref:System.ObsoleteAttribute>\-Attribut markiert, damit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn nicht aufrufen kann.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 Diese Meldung ist standardmäßig eine Warnung, da die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft von <xref:System.ObsoleteAttribute> den Wert `False` aufweist. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC41003  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie einen Aufruf von `MyBase.New()` oder `MyClass.New()` als erste Anweisung von `Sub New` in der abgeleiteten Klasse ein.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)