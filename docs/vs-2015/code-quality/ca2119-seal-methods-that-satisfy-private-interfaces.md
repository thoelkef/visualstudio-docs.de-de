---
title: 'CA2119: Versiegeln von Methoden, die private Schnittstellen erfüllen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0afa6950a6ad876cdcfdcc1a56dd143422b9d44f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544351"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein vererbbarer öffentlicher Typ stellt eine über schreibbare Methoden Implementierung einer `internal` ( `Friend` in Visual Basic)-Schnittstelle bereit.

## <a name="rule-description"></a>Beschreibung der Regel
 Schnittstellen Methoden haben öffentliche Barrierefreiheit, die nicht durch den implementierenden Typ geändert werden kann. Eine interne Schnittstelle erstellt einen Vertrag, der nicht für die Implementierung außerhalb der Assembly vorgesehen ist, die die Schnittstelle definiert. Ein öffentlicher Typ, der eine Methode einer internen Schnittstelle mit dem `virtual` - `Overridable` Modifizierer (in Visual Basic) implementiert, ermöglicht das Überschreiben der-Methode durch einen abgeleiteten Typ außerhalb der Assembly. Wenn ein zweiter Typ in der definierenden Assembly die-Methode aufruft und einen internen Vertrag erwartet, kann das Verhalten gefährdet werden, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird. Dadurch entsteht ein Sicherheitsrisiko.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird, indem Sie eine der folgenden Methoden verwenden:

- Legen Sie den deklarierenden Typ `sealed` ( `NotInheritable` in Visual Basic) ab.

- Ändern Sie den Zugriff auf den deklarierenden `internal` Typ `Friend` in (in Visual Basic).

- Entfernen Sie alle öffentlichen Konstruktoren aus dem deklarierenden Typ.

- Implementieren Sie die-Methode ohne den- `virtual` Modifizierer.

- Implementieren Sie die-Methode explizit.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn nach der sorgfältigen Überprüfung keine Sicherheitsprobleme vorhanden sind, die möglicherweise ausgenutzt werden, wenn die Methode außerhalb der Assembly überschrieben wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen-Typ,, der gegen `BaseImplementation` diese Regel verstößt.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Implementierung der virtuellen Methode des vorherigen Beispiels ausgenutzt.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Weitere Informationen
 [Schnitt](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [stellen Schnittstellen](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
