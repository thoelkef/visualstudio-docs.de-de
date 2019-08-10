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
ms.openlocfilehash: 3868061a01572d0b1adadec6619f88269d353dff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922437"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren.

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine extern sichtbare Methode dereferenziert eines der zugehörigen Verweis Argumente, ohne zu überprüfen, `null` ob`Nothing` dieses Argument (in Visual Basic) ist.

## <a name="rule-description"></a>Regelbeschreibung

Alle Verweis Argumente, die an extern sichtbare Methoden übermittelt werden, sollten `null`gegen überprüft werden. Lösen Sie ggf. <xref:System.ArgumentNullException> eine aus, wenn `null`das-Argument ist.

Wenn eine Methode von einer unbekannten Assembly aufgerufen werden kann, da Sie als öffentlich oder geschützt deklariert ist, sollten Sie alle Parameter der Methode überprüfen. Wenn die-Methode nur von bekannten Assemblys aufgerufen werden soll, sollten Sie die-Methode intern machen und <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> das-Attribut auf die Assembly anwenden, die die-Methode enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen `null`diese Regel zu beheben, überprüfen Sie jedes Verweis Argument auf.

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

Kopierkonstruktoren, die Felder oder Eigenschaften auffüllen, die Verweis Objekte sind, können auch gegen die CA1062-Regel verstoßen. Die Verletzung tritt auf, weil das kopierte Objekt, das an den Kopierkonstruktor`Nothing` übergeben wird, möglicherweise `null` (in Visual Basic) ist. Um die Verletzung aufzulösen, verwenden Sie eine statische Methode (Shared in Visual Basic), um zu überprüfen, ob das kopierte Objekt nicht NULL ist.

Im folgenden `Person` Klassen Beispiel kann das `other` -Objekt, das an den `Person` Kopierkonstruktor übergeben wird `null`, sein.

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

Im folgenden überarbeiteten `Person` Beispiel wird das `other` an den Kopierkonstruktor übergebene-Objekt zuerst auf NULL in der `PassThroughNonNull` -Methode überprüft.

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