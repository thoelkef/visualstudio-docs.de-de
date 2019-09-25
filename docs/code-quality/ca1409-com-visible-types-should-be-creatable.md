---
title: 'CA1409: Für COM sichtbare Typen müssen erstellt werden können.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54630b7fba69ef96a2c08486e535ae45d8e614b8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234766"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Für COM sichtbare Typen müssen erstellt werden können.

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Verweistyp, der speziell als sichtbar für Component Object Model (com) gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, aber keinen öffentlichen Standardkonstruktor (parameterlos).

## <a name="rule-description"></a>Regelbeschreibung
Ein Typ ohne einen öffentlichen Standardkonstruktor kann von com-Clients nicht erstellt werden. Der Zugriff auf den-Typ kann jedoch weiterhin von com-Clients erfolgen, wenn ein anderer Mittelwert zum Erstellen des Typs verfügbar ist und ihn an den Client übergibt (z. b. durch den Rückgabewert eines Methoden Aufrufes).

Die Regel ignoriert Typen, die von <xref:System.Delegate?displayProperty=fullName>abgeleitet sind.

Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen öffentlichen Standardkonstruktor <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> hinzu, oder entfernen Sie aus dem Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn andere Möglichkeiten bereitgestellt werden, um das Objekt zu erstellen und an den com-Client zu übergeben.

## <a name="related-rules"></a>Verwandte Regeln
[CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch

- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)