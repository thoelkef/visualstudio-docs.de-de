---
title: 'CA1044: Eigenschaften sollten nicht lesegeschützt sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f0e3c1cea0c1880bc13359c9b808eff0098609e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918640"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Eigenschaften sollten nicht lesegeschützt sein.

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die öffentliche oder geschützte Eigenschaft verfügt über einen Set-Accessor, jedoch verfügt nicht über einen Get-Accessor.

## <a name="rule-description"></a>Regelbeschreibung
 Erhalten bieten Sie Accessoren Lesezugriff auf eine Eigenschaft und gewähren Sie Set-Zugriffsmethoden Schreibzugriff. Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Dies ist, da einen Benutzer einen Wert festlegen zu lassen, und klicken Sie dann verhindert, dass des Benutzers anzeigen des Werts wird keine Sicherheit geboten. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Get-Accessor der Eigenschaft ein. Auch wenn das Verhalten einer nur-Schreiben-Eigenschaft erforderlich ist, sollten Sie konvertieren diese Eigenschaft in eine Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es wird empfohlen, dass Sie eine Warnung dieser Regel nicht unterdrücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadClassWithWriteOnlyProperty` ist ein Typ mit einer nur-Schreiben-Eigenschaft. `GoodClassWithReadWriteProperty` enthält den korrigierten Code.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]