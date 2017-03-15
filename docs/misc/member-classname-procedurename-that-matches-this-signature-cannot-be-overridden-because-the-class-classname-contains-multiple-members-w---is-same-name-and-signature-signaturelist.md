---
title: "Member &quot;&lt;Klassenname&gt; &lt;Prozedurname&gt;&quot;, der mit dieser Signatur &#252;bereinstimmt, kann nicht &#252;berschrieben werden, weil die Klasse &quot;&lt;Klassenname&gt;&quot; mehrere Member mit diesem Namen und dieser Signatur enth&#228;lt: &lt;Signaturliste&gt; | Microsoft Docs"
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
  - "bc30935"
  - "vbc30935"
helpviewer_keywords: 
  - "BC30935"
ms.assetid: 1165b630-668d-417d-9e18-9b8ffe7f6980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &quot;&lt;Klassenname&gt; &lt;Prozedurname&gt;&quot;, der mit dieser Signatur &#252;bereinstimmt, kann nicht &#252;berschrieben werden, weil die Klasse &quot;&lt;Klassenname&gt;&quot; mehrere Member mit diesem Namen und dieser Signatur enth&#228;lt: &lt;Signaturliste&gt;
Eine Prozedur oder Eigenschaft versucht, eine geerbte Prozedur bzw. Eigenschaft zu überschreiben, doch der Compiler findet mehrere Versionen der Basisprozedur oder Eigenschaft mit gleichem Namen und gleicher Signatur.  
  
 Dieser Fehler kann in einer Situation mit konstruierten generischen Typen auftreten, wie in den folgenden Skelettdeklarationen veranschaulicht.  
  
```  
Public Class baseClass(Of t) Public Overridable Sub doSomething(ByVal inputValue As String) End Sub Public Overridable Sub doSomething(ByVal inputValue As t) End Sub End Class Public Class derivedClass Inherits baseClass(Of String) Overrides Sub doSomething(ByVal inputValue As String) End Sub End Class  
```  
  
 Da die `derivedClass` die `baseClass` erbt, die eine `String` für den Typparameter `t` angibt, haben die beiden Versionen von `doSomething` in der `baseClass` in Bezug auf die `derivedClass` identische Signaturen. Daher kann der Compiler nicht ermitteln, welche Version überschrieben werden soll.  
  
 **Fehler\-ID:** BC30935  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie das Typargument \(oder mehrere Typargumente\), das Sie für die Basisklasse angeben, damit sich keine identischen Signaturen von Memberprozeduren oder Eigenschaften ergeben.  
  
     \- oder \-  
  
-   Wenn die Basisklasse mit dem angegebenen Satz Typargumente geerbt werden muss, sorgen Sie dafür, dass die in dieser Fehlermeldung angegebene Prozedur oder Eigenschaft nicht überschrieben wird.  
  
## Siehe auch  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)