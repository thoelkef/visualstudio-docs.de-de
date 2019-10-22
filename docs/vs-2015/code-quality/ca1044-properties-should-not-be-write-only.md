---
title: 'CA1044: Eigenschaften dürfen nicht schreibgeschützt sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa2d07337ec48e41a9d8ad82602a387159192f92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668272"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Eigenschaften sollten nicht lesegeschützt sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die öffentliche oder geschützte Eigenschaft verfügt über einen Set-Accessor, verfügt jedoch nicht über einen get-Accessor.

## <a name="rule-description"></a>Regelbeschreibung
 Get-Accessoren bieten Lesezugriff auf eine Eigenschaft, und Set-Accessoren stellen Schreibzugriff bereit. Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Der Grund hierfür ist, dass ein Benutzer einen Wert festlegen kann und die Anzeige des Werts durch den Benutzer nicht gewährleistet. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie der-Eigenschaft einen get-Accessor hinzu, um einen Verstoß gegen diese Regel zu beheben. Wenn das Verhalten einer schreibgeschützten Eigenschaft erforderlich ist, empfiehlt es sich, diese Eigenschaft in eine Methode umzuwandeln.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es wird dringend empfohlen, dass Sie eine Warnung aus dieser Regel nicht unterdrücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel ist `BadClassWithWriteOnlyProperty` ein Typ mit einer schreibgeschützten Eigenschaft. `GoodClassWithReadWriteProperty` enthält den korrigierten Code.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
