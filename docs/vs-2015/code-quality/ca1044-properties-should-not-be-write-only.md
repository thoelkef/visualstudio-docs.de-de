---
title: 'CA1044: Eigenschaften sollten nicht lesegeschützt sein | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b6d0d37d68951d556cdb575897178bd07a55a6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860837"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Eigenschaften sollten nicht lesegeschützt sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es wird dringend empfohlen, dass Sie eine Warnung dieser Regel nicht unterdrücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadClassWithWriteOnlyProperty` ist ein Typ mit einer nur-Schreiben-Eigenschaft. `GoodClassWithReadWriteProperty` enthält den korrigierten Code.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]



