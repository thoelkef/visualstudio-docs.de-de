---
title: 'CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cb38b089b432d65d74032b5ceb5ef820685557c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891920"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ ist versiegelt und deklariert eine Methode, die sowohl `virtual` (`Overridable` in Visual Basic) und nicht. Diese Regel meldet keine Verstöße für Delegattypen, die diesem Muster folgen müssen.

## <a name="rule-description"></a>Regelbeschreibung
 Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Sie können nicht per Definition aus einem versiegelten Typ eine virtuelle Methode für einen versiegelten Typ bedeutungslos erben.

 Die Visual Basic- und C#-Compiler gestatten keine Typen, die gegen diese Regel verstoßen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Methode nicht virtuell, oder ändern Sie den Typ geerbt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Verlassen den Typ im aktuellen Zustand kann dazu führen, dass Wartungsprobleme und bietet keine Vorteile.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]