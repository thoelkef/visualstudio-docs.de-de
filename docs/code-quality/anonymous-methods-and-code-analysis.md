---
title: Anonyme Methoden und Codeanalyse
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e069976badeffbce04b2f245277426441d3df2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31892702"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonyme Methoden und Codeanalyse
Ein *anonyme Methode* ist eine Methode, die keinen Namen hat. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben.

 In diesem Thema wird erläutert, wie die Codeanalyse behandelt, Warnungen und Metriken, die anonyme Methoden zugeordnet sind.

## <a name="anonymous-methods-declared-in-a-member"></a>Anonyme Methoden, die In einem Element deklariert
 Warnungen und Metriken für eine anonyme Methode, die in einem Member, z. B. eine Methode oder einen Accessor, deklariert wird sind das Element, das die Methode deklariert zugeordnet. Sie sind nicht das Element, das die Methodenaufrufe zugeordnet.

 Beispielsweise ist in die folgende Klasse, die alle Warnungen, die in der Deklaration des gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Methode1** und nicht **Methode2**.

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

## <a name="inline-anonymous-methods"></a>Inline anonyme Methoden
 Warnungen und Metriken für eine anonyme Methode, die als eine Inline-Zuweisung zu einem Feld deklariert ist werden dem Konstruktor zugeordnet. Wenn das Feld, als deklariert ist `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), die Warnungen und Metriken sind, andernfalls der Klassenkonstruktor zugeordnet, den Instanzkonstruktor zugeordnet werden.

 Z. B. in der folgenden Klasse alle Warnungen, die in der Deklaration des gefunden werden **anonymousMethod1** ausgelöst werden soll, für der implizit generierten Standardkonstruktor des **Klasse**. Während diese in gefunden **anonymousMethod2** für den Konstruktor implizit generierte Klasse angewendet werden.

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

 Eine Klasse kann Inline anonyme Methode enthalten, die ein Feld einen Wert zuweist, die mehrere Konstruktoren aufweist. So werden in diesem Fall Warnungen und Metriken alle Konstruktoren zugeordnet, wenn es sich bei diesen Konstruktor an einen anderen Konstruktor in der gleichen Klasse verkettet ist.

 Beispielsweise ist in die folgende Klasse, die alle Warnungen, die in der Deklaration des gefunden werden **AnonymousMethod** ausgelöst werden soll, für **Class(int)** und **Class(string)** jedoch nicht für **Class()**.

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

 Obwohl dies unerwartete erscheinen, kann geschieht dies, weil der Compiler eine eindeutige Methode für jeden Konstruktor ausgibt, die nicht mit einem anderen Konstruktor verkettet ist. Aufgrund dieses Verhaltens jeder Verstoß Dies tritt in **AnonymousMethod** muss separat unterdrückt werden. Dies bedeutet auch, dass wenn Sie ein neuer Konstruktor wird eingeführt, Warnungen, die zuvor für unterdrückt wurden **Class(int)** und **Class(string)** muss auch für den neuen Konstruktor unterdrückt werden.

 Sie können dieses Problem in einer von zwei Methoden umgehen. Sie deklarieren **AnonymousMethod** in einem allgemeinen Konstruktor, der alle Konstruktoren verkettet. Oder deklarieren Sie es in eine Initialisierungsmethode, die von allen Konstruktoren aufgerufen wird.

## <a name="see-also"></a>Siehe auch
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)