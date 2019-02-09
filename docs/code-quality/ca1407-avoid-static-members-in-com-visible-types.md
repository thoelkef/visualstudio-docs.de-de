---
title: 'CA1407: Statische Member in für COM sichtbaren Typen vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b09122aebdc02b9eacb32df596914a0a08a9ea9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932677"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Statische Member in für COM sichtbaren Typen vermeiden.

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ, die speziell auf Component Object Model (COM) als sichtbar markiert ist, enthält eine `public``static` Methode.

## <a name="rule-description"></a>Regelbeschreibung
 COM unterstützt keine `static` Methoden.

 Mit dieser Regel werden ignoriert, Eigenschaft und Ereignisaccessoren, Überladen von Methoden oder Methoden, die markiert sind, indem Sie entweder die <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut oder das <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut.

 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Member in öffentlichen Typen und alle Mitglieder der öffentliche Werttypen.

 Für diese Regel vorgenommen wird, eine auf Assemblyebene <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `false` "und" der Klasse - <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `true`, wie der folgende Code zeigt.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design, um eine Instanzmethode zu verwenden, die die gleiche Funktionalität wie stellt der `static` Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn ein COM-Client keinen Zugriff auf die Funktionen erfordert, die von bereitgestellte der `static` Methode.

## <a name="example-violation"></a>Beispiel für einen Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine `static` -Methode, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Kommentare
 In diesem Beispiel die **Book.FromPages** Methode kann nicht aus COM aufgerufen werden

## <a name="example-fix"></a>Korrektur für Beispiel

### <a name="description"></a>Beschreibung
 Sie können die Methode in einer Instanzmethode ändern, um die Verletzung der im vorherigen Beispiel zu beheben, allerdings, die nicht sinnvoll in dieser Instanz. Eine bessere Lösung ist, um explizit übernehmen `ComVisible(false)` auf die Methode, um anderen Entwicklern zu erleichtern, dass die Methode aus COM nicht sichtbar ist

 Im folgenden Beispiel wird <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> an die Methode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Siehe auch
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)