---
title: 'CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ec8efcc464b111de7296e11185c1f9562c749179
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927579"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden.

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Einem Component Object Model (COM) Schnittstelle deklariert überladener Methoden.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem Sie auf den Namen anfügen, einen Unterstrich "_" und eine ganze Zahl, die Reihenfolge der Deklaration der Überladung entspricht. Betrachten Sie beispielsweise die folgenden Methoden:

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

Diese Methoden werden für COM-Clients wie folgt verfügbar gemacht.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6-COM-Clients können keine Schnittstellenmethoden implementieren, mit einem Unterstrich im Namen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die überladenen Methoden, sodass die Namen eindeutig sind. Sie können auch die Schnittstelle für COM sichtbar machen durch Ändern der Zugriff auf `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) oder durch Anwenden der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> -Attributsatz auf `false`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Schnittstelle, die gegen die Regel verstößt und eine Schnittstelle, die die Regel erfüllt.

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1413: Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
- [Long-Datentyp](/dotnet/visual-basic/language-reference/data-types/long-data-type)