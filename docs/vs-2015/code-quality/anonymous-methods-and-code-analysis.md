---
title: Anonyme Methoden und Codeanalyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8b3f64a0b5f70067367e98d7e1d1471fc670099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157061"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonyme Methoden und Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *anonyme Methode* ist eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben.  
  
 In diesem Thema wird erläutert, wie die Codeanalyse verarbeitet, Warnungen und Metriken, die mit anonymen Methoden verknüpft sind.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Anonyme Methoden, die In einem Element deklariert  
 Warnungen und Metriken für eine anonyme Methode, die in einem Element, z. B. eine Methode oder der Accessor deklariert wird gehören mit dem Element, das die Methode deklariert. Sie sind nicht das Element, das die Methode ruft zugeordnet.  
  
 Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Method1** und nicht **Method2**.  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
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
  
## <a name="inline-anonymous-methods"></a>Anonyme Inlinemethoden  
 Warnungen und Metriken für eine anonyme Methode, die als eine Inline-Zuweisung an ein Feld deklariert ist, sind mit der Konstruktor verbunden. Wenn das Feld, als deklariert wird `static` (`Shared` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), die Warnungen und Metriken sind, andernfalls der Konstruktor der Klasse zugeordnet, sie sind den Instanzkonstruktor zugeordnet.  
  
 Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **anonymousMethod1** wird ausgelöst, für das implizit generierte Standard-Konstruktor von **Klasse**. Während die finden Sie in **anonymousMethod2** wird für den Konstruktor implizit generierte Klasse angewendet werden.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
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
  
 Eine Klasse kann Inline anonyme Methode enthalten, die ein Feld einen Wert zuweist, die mehrere Konstruktoren. In diesem Fall dienen diese Warn- und Metriken alle Konstruktoren zugeordnet, wenn dieser Konstruktor einen anderen Konstruktor in derselben Klasse verkettet.  
  
 Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Class(int)** und **Class(string)** jedoch nicht für **Class()** .  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
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
  
 Auch wenn dieses Verhalten vielleicht könnte, erfolgt dies, da der Compiler eine eindeutige Methode für jeden Konstruktor ausgibt, die nicht mit einem anderen Konstruktor verkettet ist. Aufgrund dieses Verhaltens eine Verletzung Dies tritt in **AnonymousMethod** müssen separat unterdrückt werden. Dies bedeutet auch, dass wenn Sie ein neuer Konstruktor wird eingeführt, Warnungen, die vorher mit unterdrückten **Class(int)** und **Class(string)** muss auch für den neuen Konstruktor unterdrückt werden.  
  
 Sie können dieses Problem auf zwei Arten umgehen. Sie können deklarieren **AnonymousMethod** in einem allgemeinen Konstruktor, der alle Konstruktoren verkettet. Oder Sie deklarieren sie in einer Initialisierungsmethode, die von allen Konstruktoren aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
