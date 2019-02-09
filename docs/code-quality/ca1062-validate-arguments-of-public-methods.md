---
title: 'CA1062: Argumente von öffentlichen Methoden validieren.'
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
ms.openlocfilehash: 274b01a67974db08d9ec016a18ec115bcfac2452
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907970"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren.

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine extern sichtbare Methode hebt den Verweis auf eines ihrer Verweisargumente ohne zu überprüfen, ob das Argument `null` (`Nothing` in Visual Basic).

## <a name="rule-description"></a>Regelbeschreibung

Alle Verweisargumente, die an extern sichtbare Methoden übergeben werden sollte aktiviert sein, für `null`. Lösen Sie ggf. eine <xref:System.ArgumentNullException> Wenn das Argument ist `null`.

Wenn eine Methode aus einer unbekannten Assembly aufgerufen werden kann, da sie öffentliche oder geschützte deklariert ist, sollten Sie alle Parameter der Methode überprüfen. Wenn die Methode nur von bekannten Assemblys aufgerufen werden soll, sollten Sie die Methode intern machen und Anwenden der <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> -Attribut auf die Assembly, die die Methode enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie jedes Verweisargument für `null`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können eine Warnung dieser Regel unterdrücken, wenn Sie sicher sind, dass die dereferenzierte Parameter durch einen anderen Aufruf der-Methode in der Funktion überprüft wurde.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt und eine Methode, die die Regel erfüllt.

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
                throw new ArgumentNullException("input");
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
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Beispiel

Kopierkonstruktoren, die Felder oder Eigenschaften, die Reference-Objekten auffüllen können auch die CA1062 Regel verletzen. Die Verletzung auftritt, da das kopierte Objekt, das an den Copy-Konstruktor übergeben wird möglicherweise `null` (`Nothing` in Visual Basic). Um die Verletzung zu beheben, verwenden Sie eine statische Methode der (Shared in Visual Basic) zu um überprüfen, ob das kopierte Objekt nicht null ist.

In der folgenden `Person` Klasse beispielsweise die `other` -Objekt, das an die `Person` Kopierkonstruktor möglicherweise `null`.

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

In den folgenden überarbeitet `Person` beispielsweise die `other` -Objekt, das an den Copy-Konstruktor übergeben wird wird zunächst überprüft, für NULL-Wert in der `PassThroughNonNull` Methode.

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
            throw new ArgumentNullException("person");
        return person;
    }
}
```