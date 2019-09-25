---
title: 'CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 84cac2f48112c43805cdd9c12a6a41cf56a8ae72
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232614"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein vererbbarer öffentlicher Typ stellt eine über schreibbare Methoden Implementierung `internal` einer`Friend` (in Visual Basic)-Schnittstelle bereit.

## <a name="rule-description"></a>Regelbeschreibung
Schnittstellen Methoden haben öffentliche Barrierefreiheit, die nicht durch den implementierenden Typ geändert werden kann. Eine interne Schnittstelle erstellt einen Vertrag, der nicht für die Implementierung außerhalb der Assembly vorgesehen ist, die die Schnittstelle definiert. Ein öffentlicher Typ, der eine Methode einer internen Schnittstelle mit dem `virtual` -`Overridable` Modifizierer (in Visual Basic) implementiert, ermöglicht das Überschreiben der-Methode durch einen abgeleiteten Typ außerhalb der Assembly. Wenn ein zweiter Typ in der definierenden Assembly die-Methode aufruft und einen internen Vertrag erwartet, kann das Verhalten gefährdet werden, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird. Dadurch entsteht ein Sicherheitsrisiko.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird, indem Sie eine der folgenden Methoden verwenden:

- Legen Sie den deklarierenden`NotInheritable` Typ `sealed` (in Visual Basic) ab.

- Ändern Sie `internal` den Zugriff auf den deklarierenden Typ`Friend` in (in Visual Basic).

- Entfernen Sie alle öffentlichen Konstruktoren aus dem deklarierenden Typ.

- Implementieren Sie die-Methode ohne `virtual` den-Modifizierer.

- Implementieren Sie die-Methode explizit.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn nach der sorgfältigen Überprüfung keine Sicherheitsprobleme vorhanden sind, die möglicherweise ausgenutzt werden, wenn die Methode außerhalb der Assembly überschrieben wird.

## <a name="example-1"></a>Beispiel 1
Das folgende Beispiel zeigt einen-Typ `BaseImplementation`,, der gegen diese Regel verstößt.

[!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
[!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
[!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Beispiel 2
Im folgenden Beispiel wird die Implementierung der virtuellen Methode des vorherigen Beispiels ausgenutzt.

[!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
[!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
[!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Siehe auch

- [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)
- [Schnittstellen](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)