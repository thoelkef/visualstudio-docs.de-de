---
title: 'CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 26a7aeca52852679797ccd5ce4de356abc289100
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029660"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein vererbbarer öffentlicher Typ stellt eine überschreibbare methodenimplementierung einer `internal` (`Friend` in Visual Basic) Schnittstelle.

## <a name="rule-description"></a>Regelbeschreibung
 Schnittstellenmethoden müssen Öffentliche zugreifbarkeit, durch den implementierenden Typ kann nicht geändert werden. Eine interne Schnittstelle erstellt einen Vertrag, der nicht vorgesehen ist, außerhalb der Assembly implementiert werden, die die Schnittstelle definiert. Ein öffentlicher Typ, der implementiert eine Methode von einer internen Schnittstelle mithilfe der `virtual` (`Overridable` in Visual Basic)-Modifizierers können die Methode, die von einem abgeleiteten Typ überschrieben werden, die außerhalb der Assembly ist. Wenn Sie ein zweiter Typ in der definierenden Assembly, die Methode aufruft und erwartet, dass einen Vertrag nur intern, möglicherweise Verhalten beeinträchtigt, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird. Dadurch wird ein Sicherheitsrisiko erstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird, indem Sie eine der folgenden:

- Ändern Sie den deklarierenden Typ `sealed` (`NotInheritable` in Visual Basic).

- Ändern Sie den Zugriff des deklarierenden Typs `internal` (`Friend` in Visual Basic).

- Entfernen Sie alle öffentliche Konstruktoren, von dem deklarierenden Typ.

- Implementieren Sie die Methode ohne Verwendung der `virtual` Modifizierer.

- Implementieren Sie explizit die Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicherer, unterdrücken Sie eine Warnung von dieser Regel, wenn Sie nach sorgfältiger Prüfung keine Sicherheitsprobleme, die vorhanden sein kann ausgenutzt werden, wenn die Methode außerhalb der Assembly überschrieben wird.

## <a name="example-1"></a>Beispiel 1
 Das folgende Beispiel zeigt einen Typ, `BaseImplementation`, die gegen diese Regel verstößt.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Beispiel 2
 Im folgende Beispiel nutzt die virtuelle Methode-Implementierung des vorherigen Beispiels.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Siehe auch

- [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)
- [Schnittstellen](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)