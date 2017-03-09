---
title: "Compilerfehler CS0730 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0730"
ms.assetid: bf291285-dc1e-4c8d-a449-119004adc088
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0730
Der Typ 'Typ' ist ein geschachtelter Typ von 'Typ' und kann daher nicht weitergeleitet werden.  
  
 Dieser Fehler wird generiert, wenn Sie versuchen, eine geschachtelte Klasse weiterzuleiten.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0730 generiert: Es besteht aus zwei Quelldateien. Kompilieren Sie zunächst die Bibliotheksdatei `CS0730a.cs`, und kompilieren Sie dann die Datei `CS0730.cs`, die auf die Bibliotheksdatei verweist.  
  
```  
// CS0730a.cs // compile with: /t:library public class Outer { public class Nested {} }  
```  
  
```  
// CS0730.cs // compile with: /t:library /r:CS0730a.dll using System.Runtime.CompilerServices; [assembly:TypeForwardedToAttribute(typeof(Outer.Nested))]   // CS0730 [assembly:TypeForwardedToAttribute(typeof(Outer))]   // OK  
```