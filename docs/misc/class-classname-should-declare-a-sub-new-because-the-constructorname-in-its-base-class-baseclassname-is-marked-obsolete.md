---
title: "Die Klasse &#39;&lt;Klassenname&gt;&#39; muss eine &#39;Sub New&#39; deklarieren, da &#39;&lt;Konstruktorname&gt;&#39; in der &#39;&lt;Basisklassenname&gt;&#39;-Basisklasse als veraltet markiert ist. | Microsoft Docs"
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
  - "bc41001"
  - "vbc41001"
helpviewer_keywords: 
  - "BC41001"
ms.assetid: b2c6b996-6d52-4963-9fee-8b6f78fc028c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Klasse &#39;&lt;Klassenname&gt;&#39; muss eine &#39;Sub New&#39; deklarieren, da &#39;&lt;Konstruktorname&gt;&#39; in der &#39;&lt;Basisklassenname&gt;&#39;-Basisklasse als veraltet markiert ist.
Eine Klassendeklaration enthält keinen Konstruktor, und der Basisklassenkonstruktor ist mit dem <xref:System.ObsoleteAttribute>\-Attribut und der Direktive versehen, dies als Warnung zu behandeln.  
  
 Wenn eine abgeleitete Klasse keinen Konstruktor deklariert, versucht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] einen impliziten parameterlosen Konstruktor zu generieren, der `MyBase.New()` aufruft. Wenn kein zugänglicher Konstruktor in der Basisklasse vorhanden ist, der ohne Argumente aufgerufen werden kann, kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen impliziten Konstruktor generieren. In diesem Fall wird der erforderliche Konstruktor mit dem <xref:System.ObsoleteAttribute>\-Attribut markiert, damit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ihn nicht aufrufen kann.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 Diese Meldung ist standardmäßig eine Warnung, da die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft von <xref:System.ObsoleteAttribute> den Wert `False` aufweist. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC41001  
  
### So beheben Sie diesen Fehler  
  
1.  Verwenden Sie `Sub New`, um in der abgeleiteten Klasse einen Konstruktor zu deklarieren.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)