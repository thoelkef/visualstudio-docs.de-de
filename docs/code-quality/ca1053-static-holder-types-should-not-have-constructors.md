---
title: 'CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fec59e1d683c7867eb1cad9ae4e796a0815200d4
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604784"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Statische Halter Typen sollten keine Standardkonstruktoren aufweisen.

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

> [!NOTE]
> Die Regel CA1053 wird in [CA1052 kombiniert: Statische Halter Typen sollten in](ca1052-static-holder-types-should-be-sealed.md) [FxCop-Analyzern](fxcop-analyzers.yml)versiegelt sein.

## <a name="cause"></a>Ursache

Ein öffentlicher oder ein eingefügter öffentlicher Typ deklariert nur statische Member und verfügt über einen Standardkonstruktor.

## <a name="rule-description"></a>Regelbeschreibung

Der Standardkonstruktor ist nicht erforderlich, da das Aufrufen statischer Member keine Instanz des Typs erfordert. Da der Typ nicht über nicht statische Member verfügt, bietet das Erstellen einer-Instanz keinen Zugriff auf die Member des Typs.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entfernen Sie den Standardkonstruktor, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Das vorhanden sein des Standardkonstruktors deutet darauf hin, dass der Typ kein statischer Typ ist.