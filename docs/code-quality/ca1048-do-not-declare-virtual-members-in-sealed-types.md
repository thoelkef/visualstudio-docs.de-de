---
title: 'CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ed0b23d62bd46a9764bfb0a3834e0decd476b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922595"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren.

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentlicher Typ ist versiegelt und deklariert eine Methode, die sowohl `virtual` (`Overridable` in Visual Basic) als auch nicht endgültig ist. Diese Regel meldet keine Verstöße gegen Delegattypen, die diesem Muster folgen müssen.

## <a name="rule-description"></a>Regelbeschreibung
Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Definitionsgemäß können Sie nicht von einem versiegelten Typ erben, sodass eine virtuelle Methode für einen versiegelten Typ bedeutungslos ist.

Die Visual Basic und C# Compiler können diese Regel nicht verletzen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, legen Sie die Methode als nicht virtuell fest, oder machen Sie den Typ vererbbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie den Typ im aktuellen Zustand belassen, kann dies zu Wartungsproblemen führen und bietet keine Vorteile.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]