---
title: "Compilerfehler CS0447 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0447
Attribute können nicht für Typargumente verwendet werden, sondern nur für Typparameter.  
  
 Dieser Fehler tritt auf, wenn Sie ein Attribut auf ein Typargument anwenden, das in einer Aufrufanweisung auftritt. Es ist zulässig, ein Attribut auf einen Typparameter in einer Klassen\- oder Methodendeklarationsanweisung wie der folgenden anzuwenden:  
  
```  
class C<[some attribute] T> {…}  
```  
  
 Dieser Fehler wird durch die folgende Codezeile generiert. Es wird davon ausgegangen, dass die in der vorherigen Codezeile definierte Klasse `C` eine statische Methode namens `MyStaticMethod` enthält.  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## Beispiel  
 Der folgende Code generiert den Fehler CS0447.  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```