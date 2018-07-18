---
title: 'CA1062: Argumente von öffentlichen Methoden validieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8393123f34bf8c33e6a65f26944640b500334dcb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900877"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine extern sichtbare Methode dereferenziert eines ihrer Verweisargumente ohne zu überprüfen, ob das Argument `null` (`Nothing` in Visual Basic).

## <a name="rule-description"></a>Regelbeschreibung

Alle an extern sichtbare Methoden übergebenen Verweisargumente sollten werden überprüft für `null`. Bei Bedarf Auslösen einer <xref:System.ArgumentNullException> Wenn das Argument ist `null`.

Wenn eine Methode, da sie öffentliche oder geschützte deklariert wird aus einer unbekannten Assembly aufgerufen werden kann, sollten Sie alle Parameter der Methode überprüfen. Wenn die Methode nur von bekannten Assemblys aufgerufen werden soll, sollten Sie ändern die Methode, interne und Anwenden der <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> -Attribut auf die Assembly, die die Methode enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie jedes Verweisargument auf `null`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie können eine Warnung dieser Regel unterdrücken, wenn Sie sicher sind, dass der dereferenziert Parameter von einem anderen Methodenaufruf in der Funktion überprüft wurde.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die die Regel verletzt und eine Methode, die die Regel erfüllt.

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

Kopierkonstruktoren, die Felder oder Eigenschaften, die Verweisobjekte sind auffüllen können auch die CA1062-Regel verletzen. Die Verletzung die tritt auf, da das kopierte Objekt, das an den Copy-Konstruktor übergeben wird möglicherweise `null` (`Nothing` in Visual Basic). Um einen Verstoß zu beheben, verwenden Sie eine statische Methode der (Shared in Visual Basic), überprüfen Sie, dass das kopierte Objekt nicht null ist.

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

Im folgenden überarbeitet `Person` beispielsweise die `other` -Objekt, das an den Copy-Konstruktor übergeben wird wird zuerst überprüft, für Null-Zeichen in der `PassThroughNonNull` Methode.

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