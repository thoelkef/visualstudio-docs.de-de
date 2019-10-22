---
title: 'CA1062: Argumente von öffentlichen Methoden validieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663645"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Argumente von öffentlichen Methoden validieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

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

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Beispiel
 In [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] erkennt diese Regel nicht, dass Parameter an eine andere Methode, die die Validierung durchführt, übermittelt werden.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Beispiel
 Kopierkonstruktoren, die Felder oder Eigenschaften auffüllen, die Verweis Objekte sind, können auch gegen die CA1062-Regel verstoßen. Die Verletzung tritt auf, weil das kopierte Objekt, das an den Kopierkonstruktor übergeben wird, `null` (`Nothing` in Visual Basic) sein kann. Um die Verletzung aufzulösen, verwenden Sie eine statische Methode (Shared in Visual Basic), um zu überprüfen, ob das kopierte Objekt nicht NULL ist.

 Im folgenden `Person`-Klassen Beispiel kann das `other`-Objekt, das an den `Person`-Kopierkonstruktor übergeben wird, `null` sein.

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
 Im folgenden überarbeiteten `Person`-Beispiel wird das `other`-Objekt, das an den Kopierkonstruktor übergeben wird, zuerst auf NULL in der `PassThroughNonNull`-Methode überprüft.

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
