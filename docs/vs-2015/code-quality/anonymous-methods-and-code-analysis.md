---
title: Anonyme Methoden und Code Analyse | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652222"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonyme Methoden und Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine *anonyme Methode* ist eine Methode, die über keinen Namen verfügt. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben.

 In diesem Thema wird erläutert, wie bei der Code Analyse Warnungen und Metriken behandelt werden, die anonymen Methoden zugeordnet sind.

## <a name="anonymous-methods-declared-in-a-member"></a>In einem Member deklarierte anonyme Methoden
 Warnungen und Metriken für eine anonyme Methode, die in einem Member deklariert wird, z. b. eine Methode oder ein Accessor, werden dem Member zugeordnet, der die Methode deklariert. Sie sind nicht mit dem Member verknüpft, der die-Methode aufruft.

 In der folgenden Klasse sollten z. b. alle Warnungen, die in der Deklaration von **AnonymousMethod** gefunden werden, für **Methode1** und nicht für **Methode2**ausgelöst werden.

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

## <a name="inline-anonymous-methods"></a>Anonyme Inline Methoden
 Warnungen und Metriken für eine anonyme Methode, die als Inline Zuweisung zu einem Feld deklariert ist, werden dem-Konstruktor zugeordnet. Wenn das Feld als `static` ( `Shared` in) deklariert ist [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , werden die Warnungen und Metriken dem Klassenkonstruktor zugeordnet; andernfalls sind Sie dem Instanzkonstruktor zugeordnet.

 In der folgenden Klasse werden z. b. alle Warnungen, die in der Deklaration von **anonymousMethod1** gefunden werden, für den implizit generierten Standardkonstruktor der- **Klasse**ausgelöst. Die in **anonymousMethod2** gefundenen werden hingegen auf den implizit generierten Klassenkonstruktor angewendet.

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

 Eine Klasse kann eine anonyme Inline Methode enthalten, die einem Feld mit mehreren Konstruktoren einen Wert zuweist. In diesem Fall werden Warnungen und Metriken allen Konstruktoren zugeordnet, es sei denn, der Konstruktor ist mit einem anderen Konstruktor in derselben Klasse verkettet.

 In der folgenden Klasse sollten z. b. alle Warnungen, die in der Deklaration von **AnonymousMethod** gefunden werden, für **Class (int)** und **Class (String)** , jedoch nicht für **Class ()** ausgelöst werden.

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

 Dies kann zwar unerwartet erscheinen, Dies tritt jedoch auf, weil der Compiler eine eindeutige Methode für jeden Konstruktor ausgibt, der nicht mit einem anderen Konstruktor verkettet ist. Aufgrund dieses Verhaltens muss jede Verletzung, die in **AnonymousMethod** auftritt, separat unterdrückt werden. Dies bedeutet auch, dass bei der Einführung eines neuen Konstruktors Warnungen, die zuvor für **Class (int)** und **Class (String)** unterdrückt wurden, auch gegen den neuen Konstruktor unterdrückt werden müssen.

 Sie können dieses Problem auf eine von zwei Arten umgehen. Sie könnten **AnonymousMethod** in einem gemeinsamen Konstruktor deklarieren, der von allen Konstruktoren verkettet ist. Oder Sie können Sie in einer Initialisierungs Methode deklarieren, die von allen Konstruktoren aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
