---
title: "Die Klasse &quot;&lt;Klassenname1&gt;&quot; muss eine &quot;Sub New&quot; deklarieren, da ihre Basisklasse &quot;&lt;Klassenname2&gt;&quot; mehr als eine zugreifbare &quot;Sub New&quot; hat, die ohne Argumente aufgerufen werden kann. | Microsoft Docs"
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
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Klasse &quot;&lt;Klassenname1&gt;&quot; muss eine &quot;Sub New&quot; deklarieren, da ihre Basisklasse &quot;&lt;Klassenname2&gt;&quot; mehr als eine zugreifbare &quot;Sub New&quot; hat, die ohne Argumente aufgerufen werden kann.
Eine abgeleitete Klasse deklariert keinen Konstruktor, und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kann keinen Konstruktor generieren, da der aufzurufende Basisklassenkonstruktor nicht ermittelt werden kann.  
  
 Wenn eine abgeleitete Klasse keinen Konstruktor deklariert, versucht [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], einen impliziten parameterlosen Konstruktor zu generieren, der `MyBase.New()` aufruft. Wenn in der Basisklasse kein zugreifbarer Konstruktor vorhanden ist, der ohne Argumente aufgerufen werden kann \(bzw. wenn mehrere vorhanden sind\), kann [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keinen impliziten Konstruktor generieren.  
  
 Diese Situation kann z. B. auftreten, wenn ein Basisklassenkonstruktor über ein einzelnes `Optional`\-Argument und ein anderer über ein einzelnes `ParamArray`\-Argument verfügt. Jeder dieser Konstruktoren kann ohne Argumente aufgerufen werden.  
  
 **Fehler\-ID:** BC32036  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren und implementieren Sie mindestens einen `Sub New`\-Konstruktor an einer beliebigen Stelle in der abgeleiteten Klasse.  
  
2.  Fügen Sie einen Aufruf eines Basisklassenkonstruktors `MyBase.New()` als erste Zeile jedes `Sub New` hinzu.  
  
## Siehe auch  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)