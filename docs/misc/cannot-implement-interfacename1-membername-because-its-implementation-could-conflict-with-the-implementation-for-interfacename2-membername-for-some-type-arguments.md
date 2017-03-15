---
title: "&quot;&lt;Schnittstellenname1&gt;.&lt;Membername&gt;&quot; kann nicht implementiert werden, da die Implementierung zu einem Konflikt mit der Implementierung einiger Typargumente von &quot;&lt;Schnittstellenname2&gt;.&lt;Membername&gt;&quot; f&#252;hren k&#246;nnte | Microsoft Docs"
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
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Schnittstellenname1&gt;.&lt;Membername&gt;&quot; kann nicht implementiert werden, da die Implementierung zu einem Konflikt mit der Implementierung einiger Typargumente von &quot;&lt;Schnittstellenname2&gt;.&lt;Membername&gt;&quot; f&#252;hren k&#246;nnte
Eine Klasse implementiert mehrere generische Schnittstellen, von denen eine von einer anderen erbt, und zwei Implementierungen eines Schnittstellenmembers können einen Konflikt mit bestimmten Werten von Typargumenten verursachen.  
  
 Dieser Fehler kann durch die folgenden Anweisungen generiert werden.  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 Da `iFace2` von `iFace1` erbt \(unter Verwendung des eigenen Typparameters `u`\), würde `testClass` zwei Versionen von `iFace1.testSub` mit identischen Signaturen implementieren, wenn dasselbe Typargument an `y` und `z` übergeben würde. Dies würde zu einer Mehrdeutigkeit in Bezug auf die Version führen, auf die zugegriffen werden soll.  
  
 **Fehler\-ID:** BC32125  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Vererbungsstruktur der Schnittstellen so, dass `iFace1` nicht mit zwei verschiedenen Typargumenten implementiert werden kann.  
  
     \- oder \-  
  
-   Entfernen Sie die `Implements`\-Anweisung aus einer der Schnittstellen, die zum Konflikt bei der Implementierung führen.  
  
## Siehe auch  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)