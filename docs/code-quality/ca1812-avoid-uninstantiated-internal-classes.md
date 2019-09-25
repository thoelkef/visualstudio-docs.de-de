---
title: 'CA1812: Nicht instanziierte interne Klassen vermeiden.'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233609"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden.

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein interner Typ (auf Assemblyebene) wird nie instanziiert.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel versucht, einen-Konstruktoren des-Typs aufzurufen, und meldet eine Verletzung, wenn kein-Rückruf gefunden wird.

Die folgenden Typen werden von dieser Regel nicht untersucht:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Vom Compiler ausgegebene Array Typen

- Typen, die nicht instanziiert werden können und nur [`static`](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared))-Methoden definieren.

Wenn Sie das <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die Assembly anwenden, die analysiert wird, kennzeichnet diese Regel keine Typen, die als [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) gekennzeichnet sind, da ein Feld möglicherweise von einer Friend-Assembly verwendet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie Code hinzu, der ihn verwendet. Wenn der Typ nur `static` Methoden enthält, fügen Sie einen der folgenden Werte zum-Typ hinzu, um zu verhindern, dass der Compiler einen standardmäßigen öffentlichen Instanzkonstruktor ausgibt:

- Der `static` -Modifizierer für C# Typen, die .NET Framework 2,0 oder höher als Ziel haben.

- Ein privater Konstruktor für Typen, die .NET Framework die Versionen 1,0 und 1,1 als Ziel haben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die-Klasse wird durch spät gebundene Reflektionsmethoden wie <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>erstellt.

- Die-Klasse wird automatisch von der Runtime oder ASP.NET erstellt. Einige Beispiele für automatisch erstellte Klassen sind solche, die <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName>implementieren.

- Die-Klasse wird als Typparameter übergeben, der über [ `new` ](/dotnet/csharp/language-reference/keywords/new-constraint)eine-Einschränkung verfügt. Das folgende Beispiel wird durch die Regel CA1812 gekennzeichnet:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Verwandte Regeln

- [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)