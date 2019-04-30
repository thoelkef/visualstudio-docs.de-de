---
title: 'CA1812: Nicht instanziierte interne Klassen vermeiden.'
ms.date: 11/04/2016
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
ms.openlocfilehash: 08d8b907e4a211b0735f07377c21dec1c0a982c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796903"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden.

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.

## <a name="rule-description"></a>Regelbeschreibung

Mit dieser Regel versucht, einen Aufruf eines Konstruktors den Typ zu finden, und gibt einen Verstoß aus, wenn kein Aufruf gefunden wird.

Die folgenden Typen werden nicht durch diese Regel überprüft:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Compilerfehler ausgegebenen Arraytypen

- Typen, die nicht instanziiert werden kann, und definieren `static` (`Shared` in Visual Basic) Methoden nur.

Wenn Sie anwenden <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die Assembly, die analysiert wird, mit dieser Regel treten nicht für Konstruktoren, die als markiert sind `internal` , da Sie nicht erkennen können, ob ein Feld von einem anderen verwendeten `friend` Assembly.

Obwohl Sie Umgehung dieser Einschränkung in der Visual Studio-Codeanalyse nicht möglich, wird der externe eigenständige FxCop auf interne Konstruktoren auftreten, wenn alle `friend` Assembly in der Analyse vorhanden ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code, der verwendet wird. Wenn der Typ nur statische Methoden enthält, fügen Sie eine der folgenden in den Typ aus, um zu verhindern, dass den Compiler einen Standardkonstruktor für die öffentliche Instanz ausgeben:

- Ein privater Konstruktor für Typen, die .NET Framework-1.0 und 1.1 Versionen.

- Die `static` (`Shared` in Visual Basic)-Modifizierer für Typen, die auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die Klasse wird durch für spät gebundene Reflektionsmethoden erstellt, wie z. B. <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Die Klasse wird automatisch erstellt, von der Laufzeit oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Z. B. Klassen, in denen <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Die Klasse wird als ein generischer Typparameter übergeben, die eine neue Einschränkung aufweist. Beispielsweise wird im folgenden Beispiel wird diese Regel ausgelöst.

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
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  In diesen Fällen wird empfohlen, dass Sie diese Warnung unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln

[CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)