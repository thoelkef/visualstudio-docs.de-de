---
title: 'CA1062: Argumente von öffentlichen Methoden validieren'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 43aa94f67e17a3de51635840419e36ef38db41df
ms.sourcegitcommit: e82baa50bf5a65858c410882c2e86a552c2c1921
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381017"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine extern sichtbare Methode dereferenziert eines der zugehörigen Verweis Argumente, ohne zu überprüfen, ob dieses Argument `null` (`Nothing` in Visual Basic) ist.

## <a name="rule-description"></a>Regelbeschreibung

Alle Verweis Argumente, die an extern sichtbare Methoden übermittelt werden, sollten auf `null` überprüft werden. Lösen Sie ggf. eine <xref:System.ArgumentNullException> aus, wenn das Argument `null` ist.

Wenn eine Methode von einer unbekannten Assembly aufgerufen werden kann, da Sie als öffentlich oder geschützt deklariert ist, sollten Sie alle Parameter der Methode überprüfen. Wenn die-Methode nur von bekannten Assemblys aufgerufen werden soll, sollten Sie die-Methode intern machen und das <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>-Attribut auf die Assembly anwenden, die die-Methode enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie jedes Verweis Argument auf `null`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie können eine Warnung aus dieser Regel unterdrücken, wenn Sie sicher sind, dass der Dereferenzierte Parameter von einem anderen Methoden aufrufin der Funktion überprüft wurde.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die die Regel erfüllt.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException(nameof(input));
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException(NameOf(input))
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Beispiel

Kopierkonstruktoren, die Felder oder Eigenschaften auffüllen, die Verweis Objekte sind, können auch gegen die CA1062-Regel verstoßen. Die Verletzung tritt auf, weil das kopierte Objekt, das an den Kopierkonstruktor übergeben wird, `null` (`Nothing` in Visual Basic) sein kann. Um die Verletzung aufzulösen, verwenden Sie eine statische Methode (Shared in Visual Basic), um zu überprüfen, ob das kopierte Objekt nicht NULL ist.

Im folgenden `Person`-Klassen Beispiel kann das `other`-Objekt, das an den `Person`-Kopierkonstruktor übergeben wird, `null` sein.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Beispiel

Im folgenden überarbeiteten `Person`-Beispiel wird das `other`-Objekt, das an den Kopierkonstruktor übergeben wird, zuerst auf NULL in der `PassThroughNonNull`-Methode überprüft.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException(nameof(person));
        return person;
    }
}
```