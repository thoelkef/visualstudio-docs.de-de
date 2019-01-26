---
title: 'CA1409: Für COM sichtbare Typen müssen erstellt werden können.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 4197feae7f13e82ab786cbb901c9216fa1a98353
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996440"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Für COM sichtbare Typen müssen erstellt werden können.

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Verweistyp handelt, der speziell auf Component Object Model (COM) als sichtbar markiert ist, enthält einen öffentlichen parametrisierten Konstruktor aber enthält keine öffentlichen (parameterlosen) Standardkonstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht von COM-Clients erstellt werden. Der Typ kann jedoch immer noch von COM-Clients zugegriffen werden, wenn ein anderes Mittel verfügbar ist, erstellen Sie den Typ und an dem Client (z. B. über den Rückgabewert eines Methodenaufrufs) übergeben.

 Die Regel ignoriert Typen, die abgeleitet sind <xref:System.Delegate?displayProperty=fullName>.

 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Member in öffentlichen Typen und alle Mitglieder der öffentliche Werttypen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen öffentlichen Standardkonstruktor hinzu, oder entfernen Sie die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> vom Typ.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn andere Möglichkeiten zum Erstellen und übergeben das Objekt an dem COM-Client bereitgestellt werden.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch

- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)