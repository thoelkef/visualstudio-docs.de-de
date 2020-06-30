---
title: 'CA1409: für COM sichtbare Typen sollten erstellbar sein | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547328"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Für COM sichtbare Typen müssen erstellt werden können.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Verweistyp, der speziell als sichtbar für Component Object Model (com) gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, aber keinen öffentlichen Standardkonstruktor (parameterlos).

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Typ ohne einen öffentlichen Standardkonstruktor kann von com-Clients nicht erstellt werden. Der Zugriff auf den-Typ kann jedoch weiterhin von com-Clients erfolgen, wenn ein anderer Mittelwert zum Erstellen des Typs verfügbar ist und ihn an den Client übergibt (z. b. durch den Rückgabewert eines Methoden Aufrufes).

 Die Regel ignoriert Typen, die von abgeleitet sind <xref:System.Delegate?displayProperty=fullName> .

 Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen öffentlichen Standardkonstruktor hinzu, oder entfernen Sie <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> aus dem Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn andere Möglichkeiten bereitgestellt werden, um das Objekt zu erstellen und an den com-Client zu übergeben.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Weitere Informationen
 [Qualifizieren von .NET-Typen für die Interoperation](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
