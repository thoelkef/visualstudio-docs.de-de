---
title: Anonyme Methode codeanalysewarnungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a10c5baaed3a98e44d581b6ddb8d6e3a1883d079
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940489"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonyme Methoden und Codeanalyse

Ein *anonyme Methode* ist eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. In diesem Artikel wird erläutert, wie Code Analysis für Warnungen und Metriken für anonyme Methoden behandelt.

## <a name="anonymous-methods-declared-in-a-member"></a>Anonyme Methoden, die In einem Element deklariert

Warnungen und Metriken für eine anonyme Methode, die in einem Element, z. B. eine Methode oder der Accessor deklariert wird gehören mit dem Element, das die Methode deklariert. Sie sind nicht das Element, das die Methode ruft zugeordnet.

Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Method1** und nicht **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
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

Warnungen und Metriken für eine anonyme Methode, die als eine Inline-Zuweisung an ein Feld deklariert ist, sind mit der Konstruktor verbunden. Wenn das Feld, als deklariert wird `static` (`Shared` in Visual Basic), die Warnungen und Metriken der Konstruktor der Klasse zugeordnet sind. Andernfalls sind sie mit der Instanzkonstruktor verknüpft.

Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **anonymousMethod1** wird ausgelöst, für das implizit generierte Standard-Konstruktor von **Klasse**. Warnungen, die im befinden **anonymousMethod2** wird für den Konstruktor implizit generierte Klasse angewendet werden.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
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

Z. B. in der folgenden Klasse, alle Warnungen, die in der Deklaration der gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Class(int)** und **Class(string)**, aber nicht für **Class()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
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

Für die Konstruktoren werden Warnungen ausgelöst, da der Compiler eine eindeutige Methode für jeden Konstruktor ausgibt, das nicht an einen anderen Konstruktor verkettet ist. Aufgrund dieses Verhaltens eine Verletzung Dies tritt in **AnonymousMethod** müssen separat unterdrückt werden. Dies bedeutet auch, dass wenn Sie ein neuer Konstruktor wird eingeführt, Warnungen, die vorher mit unterdrückten **Class(int)** und **Class(string)** muss auch für den neuen Konstruktor unterdrückt werden.

Sie können dieses Problem auf zwei Arten umgehen:

- Deklarieren Sie **AnonymousMethod** in einem allgemeinen Konstruktor, der alle Konstruktoren verkettet.
- Deklarieren Sie **AnonymousMethod** eine Initialisierungsmethode, die von allen Konstruktoren aufgerufen wird.

## <a name="see-also"></a>Siehe auch

- [Analysieren der Qualität von verwaltetem Code](../code-quality/code-analysis-for-managed-code-overview.md)