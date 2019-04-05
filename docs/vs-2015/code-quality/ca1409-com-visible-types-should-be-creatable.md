---
title: 'CA1409: Für COM sichtbare Typen erstellt werden soll | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b6112b559a1a00955833a563e819f6784d95d2d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959594"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Für COM sichtbare Typen müssen erstellt werden können.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn andere Möglichkeiten zum Erstellen und übergeben das Objekt an dem COM-Client bereitgestellt werden.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch
 [Qualifizieren von .NET-Typen für die Interoperation](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
