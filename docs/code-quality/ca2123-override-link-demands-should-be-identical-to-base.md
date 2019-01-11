---
title: 'CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50ca27f9c6cf15c663514588a0c08bd5b91e3bd0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882090"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ überschreibt eine Methode oder eine Schnittstelle implementiert und verfügt nicht über die gleichen [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) wie die Schnittstelle oder eine virtuelle Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Ein Verstoß wird gemeldet, wenn die-Methode oder die Basismethode einen Linkaufruf enthält, und das andere nicht.

 Wenn diese Regel verletzt wird, kann ein böswilliger Aufrufer den Linkaufruf umgehen, lediglich durch Aufruf der ungesicherten Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie den gleichen Linkaufruf auf die Methode zum Überschreiben oder die Implementierung aus. Wenn dies nicht möglich ist, markieren Sie die Methode mit einer vollständigen Anforderung aus, oder entfernen Sie das Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt verschiedene Verstöße gegen diese Regel.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)