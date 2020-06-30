---
title: 'CA1033: Schnittstellen Methoden sollten von untergeordneten Typen aufgerufen werden können | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542297"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an.

## <a name="rule-description"></a>Beschreibung der Regel
 Beachten Sie einen Basistyp, der eine öffentliche Schnittstellen Methode explizit implementiert. Ein Typ, der vom Basistyp abgeleitet wird, kann nur über einen Verweis auf die aktuelle Instanz (in c#) auf die geerbte Schnittstellen Methode zugreifen `this` , die in die-Schnittstelle umgewandelt wird. Wenn der abgeleitete Typ (explizit) die geerbte Schnittstellen Methode erneut implementiert, kann auf die Basis Implementierung nicht mehr zugegriffen werden. Durch den Aufruf über den aktuellen Instanzverweis wird die abgeleitete Implementierung aufgerufen. Dies bewirkt eine Rekursion und einen eventuellen Stapelüberlauf.

 Diese Regel meldet keine Verstöße gegen eine explizite Implementierung von, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Wenn eine extern sichtbare- `Close()` oder- `System.IDisposable.Dispose(Boolean)` Methode bereitgestellt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie eine neue Methode, die die gleiche Funktionalität verfügbar macht und für abgeleitete Typen sichtbar ist, oder ändern Sie zu einer nicht expliziten Implementierung. Wenn ein Breaking Change akzeptabel ist, besteht eine Alternative darin, den Typ versiegelt zu machen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn eine extern sichtbare Methode bereitgestellt wird, die über die gleiche Funktionalität, aber einen anderen Namen als die explizit implementierte Methode verfügt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ViolatingBase` , der gegen die Regel verstößt, und einen Typ, `FixedBase` , der eine Korrektur für die Verletzung anzeigt.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 [Schnittstellen](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
