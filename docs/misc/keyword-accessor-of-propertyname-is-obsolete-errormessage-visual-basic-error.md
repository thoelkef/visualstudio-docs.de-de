---
title: "Die &#39;&lt;Schl&#252;sselwort&gt;&#39;-Zugriffsmethode von &#39;&lt;Eigenschaftenname&gt;&#39; ist veraltet: &#39;&lt;Fehlermeldung&gt;&#39; (Visual Basic-Fehler) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &#39;&lt;Schl&#252;sselwort&gt;&#39;-Zugriffsmethode von &#39;&lt;Eigenschaftenname&gt;&#39; ist veraltet: &#39;&lt;Fehlermeldung&gt;&#39; (Visual Basic-Fehler)
Eine Anweisung versucht, eine Eigenschaft zu lesen oder zu schreiben, für die die entsprechende Prozedur mit dem <xref:System.ObsoleteAttribute>\-Attribut und mit der Direktive gekennzeichnet wurde, diese als Fehler zu behandeln.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 **Fehler\-ID:** BC30911  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die angegebene Fehlermeldung, und ergreifen Sie entsprechende Maßnahmen.  
  
2.  Stellen Sie sicher, dass der Eigenschaftenname im Quellcodeverweis richtig geschrieben ist.  
  
3.  Vermeiden Sie es, auf eine Weise \(durch Lesen oder Schreiben\) auf die Eigenschaft zuzugreifen, die zur Generierung dieser Nachricht geführt hat.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)