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
ms.openlocfilehash: a0d55af3c5522c6bb9aa3ad8a023f070c187ca6f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714267"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden.

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein interner (auf Assemblyebene) Typ wird nie instanziiert.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel versucht, einen Aufruf eines Konstruktors den Typ zu finden und einen Verstoß gemeldet, wenn kein Aufruf gefunden wird.

Die folgenden Typen werden nicht durch diese Regel überprüft:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Compilerfehler ausgegebenen Arraytypen

- Typen, die nicht instanziiert werden und nur definieren [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) Methoden.

Wenn Sie anwenden, die <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die Assembly, die analysiert wird, wird diese Regel nicht als markierten Typen gekennzeichnet [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` in Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), da möglicherweise ein Feld von Friend-Assembly verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie Code, der verwendet wird. Wenn der Typ nur enthält `static` Methoden, Hinzufügen eines der folgenden in den Typ aus, um zu verhindern, dass den Compiler einen Standardkonstruktor für die öffentliche Instanz ausgeben:

- Die `static` Modifizierer für C# Typen, die auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] oder höher.

- Ein privater Konstruktor für Typen, die .NET Framework-1.0 und 1.1 Versionen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die Klasse wird durch für spät gebundene Reflektionsmethoden erstellt, wie z. B. <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Die Klasse wird von der Laufzeit oder ASP.NET automatisch erstellt. Einige Beispiele für automatisch erstellte Klassen sind diejenigen, die implementieren <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Die Klasse wird übergeben, wie ein Typparameter, die eine [ `new` Einschränkung](/dotnet/csharp/language-reference/keywords/new-constraint). Im folgende Beispiel werden durch Regel CA1812 gekennzeichnet:

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