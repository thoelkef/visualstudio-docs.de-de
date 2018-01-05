---
title: "CA1062: Argumente von öffentlichen Methoden validieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb659fa8bfd18d8caf4a7473f6cd53809d0a126b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 In [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], diese Regel erkennt nicht, dass Parameter an eine andere Methode übergeben werden, die die Validierung ausführt.  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
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