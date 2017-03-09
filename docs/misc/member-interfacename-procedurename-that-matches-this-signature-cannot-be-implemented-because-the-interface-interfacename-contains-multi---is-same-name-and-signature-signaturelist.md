---
title: "Member &#39;&lt;Schnittstellenname&gt;.&lt;Prozedurname&gt;&#39;, der mit dieser Signatur &#252;bereinstimmt, kann nicht implementiert werden, weil die Schnittstelle &#39;&lt;Schnittstellenname&gt;&#39; mehrere Member mit diesem Namen und dieser Signatur enth&#228;lt: &lt;Signaturliste&gt; | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &#39;&lt;Schnittstellenname&gt;.&lt;Prozedurname&gt;&#39;, der mit dieser Signatur &#252;bereinstimmt, kann nicht implementiert werden, weil die Schnittstelle &#39;&lt;Schnittstellenname&gt;&#39; mehrere Member mit diesem Namen und dieser Signatur enth&#228;lt: &lt;Signaturliste&gt;
Eine Prozedur oder Eigenschaft versucht, eine Prozedur bzw. Eigenschaft zu implementieren, die in einer implementierten Schnittstelle definiert ist, doch der Compiler findet mehrere Versionen der Schnittstellenprozedur oder \-eigenschaft mit gleichem Namen und gleicher Signatur.  
  
 Dieser Fehler kann in einer Situation mit konstruierten generischen Typen auftreten, wie in den folgenden Skelettdeklarationen veranschaulicht.  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 Da die `implementingClass` die `baseInterface` implementiert, die eine `String` für den Typparameter `t` angibt, haben die beiden Versionen von `doSomething` in der `baseInterface` in Bezug auf die `implementingClass` identische Signaturen. Daher kann der Compiler nicht ermitteln, welche Version implementiert werden soll.  
  
 **Fehler\-ID:** BC30937  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie das Typargument \(oder mehrere Typargumente\), das Sie für die Basisklasse angeben, damit sich keine identischen Signaturen von Memberprozeduren oder Eigenschaften ergeben.  
  
     \- oder \-  
  
-   Implementieren Sie diese Basisklasse nicht. Sie können sie nicht mit dem von Ihnen verwendeten Satz von Typargumenten implementieren, da Sie jeden einzelnen seiner Member implementieren müssen.  
  
## Siehe auch  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be)