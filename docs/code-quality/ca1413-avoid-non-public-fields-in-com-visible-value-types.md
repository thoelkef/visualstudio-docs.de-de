---
title: 'CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 78152c3ee5825c34ea47e2267370720e698212dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996466"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Werttyp, der speziell zu Component Object Model (COM) als sichtbar markiert ist deklariert, ein nicht öffentliches Instanzfeld.

## <a name="rule-description"></a>Regelbeschreibung
 Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt des Felds für Daten, die nicht verfügbar gemacht werden, oder müssen, das Design oder unbeabsichtigte Auswirkungen, aus.

 Standardmäßig sind alle öffentlichen Werttypen für COM sichtbar. Um falsch positive Ergebnisse zu reduzieren, erfordert mit dieser Regel jedoch die COM-Sichtbarkeit des Typs explizit angegeben werden. Die übergeordnete Assembly muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ markiert werden muss, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben und das Feld ausgeblendet, ändern Sie den Werttyp in einen Verweistyp handelt, oder entfernen Sie die <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut vom Typ.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn öffentliche Offenlegung des Felds akzeptabel ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)
- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)