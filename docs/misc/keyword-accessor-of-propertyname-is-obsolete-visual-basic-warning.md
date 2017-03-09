---
title: "Der &lt;Schl&#252;sselwort&gt;-Accessor von &quot;&lt;Eigenschaftenname&gt;&quot; ist veraltet (Visual Basic-Warnung) | Microsoft Docs"
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
  - "vbc40020"
  - "bc40020"
helpviewer_keywords: 
  - "BC40020"
ms.assetid: 005440f4-6e82-421c-b2ce-9c5139325bac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &lt;Schl&#252;sselwort&gt;-Accessor von &quot;&lt;Eigenschaftenname&gt;&quot; ist veraltet (Visual Basic-Warnung)
Eine Anweisung versucht, eine Eigenschaft zu lesen oder zu schreiben, für die die entsprechende Prozedur mit dem <xref:System.ObsoleteAttribute>\-Attribut und mit der Direktive gekennzeichnet wurde, diese als Warnung zu behandeln.  
  
 Sie können jedes beliebige Programmierelement als nicht mehr in Gebrauch kennzeichnen, indem Sie <xref:System.ObsoleteAttribute> darauf anwenden. Dabei können Sie die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft des Attributs entweder auf `True` oder `False` festlegen. Wenn Sie sie auf `True` festlegen, behandelt der Compiler den Versuch, das Element zu verwenden, als Fehler. Wenn Sie sie auf `False` festlegen oder die Standardeinstellung `False` übernehmen, gibt der Compiler bei dem Versuch, das Element zu verwenden, eine Warnung aus.  
  
 Diese Meldung ist standardmäßig eine Warnung, da die <xref:System.ObsoleteAttribute.IsError%2A>\-Eigenschaft von <xref:System.ObsoleteAttribute>`False` ist. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40020  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Eigenschaftenname im Quellcodeverweis richtig geschrieben ist.  
  
2.  Vermeiden Sie es, auf eine Weise \(durch Lesen oder Schreiben\) auf die Eigenschaft zuzugreifen, durch die diese Nachricht generiert wurde.  
  
## Siehe auch  
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)