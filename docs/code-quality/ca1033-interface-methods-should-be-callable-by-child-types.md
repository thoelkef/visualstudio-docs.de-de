---
title: 'CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6d1fa4152b0906db89efbb4df68356c58c60416
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996528"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an.

## <a name="rule-description"></a>Regelbeschreibung
 Erwägen Sie einen Basistyp, der eine öffentliche Schnittstelle explizit implementiert. Ein Typ, der vom Basistyp abgeleitet ist, kann die geerbte Schnittstelle-Methode zugreifen, nur über einen Verweis auf die aktuelle Instanz (`this` in c#), die die Schnittstelle umgewandelt wird. Wenn der abgeleitete Typ (explizit) die Methode die geerbte Schnittstelle reimplements, kann die basisimplementierung nicht mehr zugegriffen werden. Der Aufruf über die aktuelle Instanz Referenz wird die abgeleitete Implementierung aufgerufen wird. Dies bewirkt, dass Rekursion und letztlich zu einem Stapelüberlauf.

 Diese Regel meldet sich nicht auf einen Verstoß gegen eine explizite Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Wenn eine extern sichtbare `Close()` oder `System.IDisposable.Dispose(Boolean)` Methode wird bereitgestellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie eine neue Methode, die stellt die gleiche Funktionalität und für abgeleitete Typen sichtbar ist, oder ändern Sie in einer Implementierung verwenden. Wenn eine wichtige Änderung akzeptabel ist, ist eine Alternative, um den Typ versiegelt stellen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist eine Warnung dieser Regel zu unterdrücken, wenn eine extern sichtbare Methode angegeben wird, die die gleiche Funktionalität aber einen anderen Namen als die explizit implementierte Methode sicher.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ViolatingBase`, die gegen die Regel und einen Typ, `FixedBase`, zeigt, dass eine Lösung für die Verletzung.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)