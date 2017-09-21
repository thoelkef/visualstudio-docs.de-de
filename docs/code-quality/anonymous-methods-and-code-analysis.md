---
title: "Anonyme Methoden und Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anonyme Methoden, Codeanalyse"
  - "Codeanalyse, Anonyme Methoden"
  - "Methoden, Anonyme"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Anonyme Methoden und Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Als *anonyme Methode* wird eine Methode ohne Namen bezeichnet.  Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben.  
  
 In diesem Thema wird erläutert, wie Warnungen und Metriken in Zusammenhang mit anonymen Methoden von der Codeanalyse behandelt werden.  
  
## In einem Member deklarierte anonyme Methoden  
 Warnungen und Metriken für eine anonyme Methode, die in einem Member deklariert ist, z. B. als Methode oder Accessor, sind mit dem Member verknüpft, durch den die Methode deklariert wird.  Mit dem Member, der die Methode aufruft, sind sie nicht verknüpft.  
  
 In der folgenden Klasse sollte beispielsweise jede Warnung in der Deklaration von **anonymousMethod** für **Method1** und nicht für **Method2** ausgelöst werden.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## Anonyme Inlinemethoden  
 Warnungen und Metriken für eine anonyme Methode, die als Inlinezuweisung für ein Feld deklariert ist, sind mit dem Konstruktor verknüpft.  Wenn das Feld als `static` \(`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) deklariert ist, sind Warnungen und Metrikdaten mit dem Klassenkonstruktor verknüpft, andernfalls sind sie mit dem Instanzenkonstruktor verknüpft.  
  
 In der folgenden Klasse werden beispielsweise alle Warnungen in der Deklaration von **anonymousMethod1** für den implizit generierten Standardkonstruktor von **Class** ausgelöst.  Warnungen in **anonymousMethod2** werden jedoch für den implizit generierten Klassenkonstruktor angewendet.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Eine Klasse könnte beispielsweise eine anonyme Inlinemethode enthalten, durch die einem Feld, das über mehrere Konstruktoren verfügt, ein Wert zugewiesen wird.  In diesem Fall sind Warnungen und Metriken mit allen Konstruktoren verknüpft, sofern der Konstruktor nicht mit einem anderen Konstruktor in derselben Klasse verknüpft ist.  
  
 In der folgenden Klasse müssen beispielsweise alle Warnungen in der Deklaration von **anonymousMethod** für **Class\(int\)** und **Class\(string\)** und nicht für **Class\(\)** ausgelöst werden.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Dieses Verhalten scheint unerwartet zu sein, tritt jedoch auf, weil der Compiler eine eindeutige Methode für jeden Konstruktor ausgibt, der nicht mit einem anderen Konstruktor verkettet ist.  Aufgrund dieses Verhaltens muss jede Verletzung, die in **anonymousMethod** auftritt, einzeln unterdrückt werden.  Dies bedeutet auch, dass Warnungen, die zuvor für **Class\(int\)** und **Class\(string\)** unterdrückt wurden, bei Einführung eines neuen Konstruktors auch für den neuen Konstruktor unterdrückt werden müssen.  
  
 Sie können dieses Problem auf zwei Weisen umgehen.  Sie könnten **anonymousMethod** in einem allgemeinen Konstruktor deklarieren, durch den alle Konstruktoren verkettet werden.  Alternativ können Sie die Methode in einer Initialisierungsmethode deklarieren, die von allen Konstruktoren aufgerufen wird.  
  
## Siehe auch  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)