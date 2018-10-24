---
title: 'CA1062: Argumente von öffentlichen Methoden validieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7d5b5039c08e27dd97c0119948c87d7295756d7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811976"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung dieser Regel unterdrücken, wenn Sie sicher sind, dass die dereferenzierte Parameter durch einen anderen Aufruf der-Methode in der Funktion überprüft wurde.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt und eine Methode, die die Regel erfüllt.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Beispiel
 In [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], diese Regel erkennt nicht, dass die Parameter an eine andere Methode übergeben werden, die die Validierung ausführt.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Beispiel
 Kopierkonstruktoren, die Felder oder Eigenschaften, die Reference-Objekten auffüllen können auch die CA1062 Regel verletzen. Die Verletzung auftritt, da das kopierte Objekt, das an den Copy-Konstruktor übergeben wird möglicherweise `null` (`Nothing` in Visual Basic). Um die Verletzung zu beheben, verwenden Sie eine statische Methode der (Shared in Visual Basic) zu um überprüfen, ob das kopierte Objekt nicht null ist.

 In der folgenden `Person` Klasse beispielsweise die `other` -Objekt, das an die `Person` Kopierkonstruktor möglicherweise `null`.

```

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

```
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



