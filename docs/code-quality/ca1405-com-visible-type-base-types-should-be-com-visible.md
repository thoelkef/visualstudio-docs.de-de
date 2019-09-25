---
title: 'CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234953"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein.

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Dependsonfix|

## <a name="cause"></a>Ursache
Ein Component Object Model sichtbarer Typ (com) ist von einem Typ abgeleitet, der nicht für com sichtbar ist.

## <a name="rule-description"></a>Regelbeschreibung
Wenn ein durch COM sichtbarer Typ Elemente in einer neuen Version hinzufügt, muss er strenge Richtlinien einhalten, um zu vermeiden, dass com-Clients, die an die aktuelle Version gebunden sind, unterbrochen werden Ein Typ, der für COM unsichtbar ist, setzt voraus, dass er diese com-Versions Regeln beim Hinzufügen neuer Member nicht befolgt. Wenn ein für COM sichtbarer Typ jedoch vom COM-unsichtbar-Typ abgeleitet ist und eine Klassen <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> Schnittstelle <xref:System.Runtime.InteropServices.ClassInterfaceType> von oder (Standard) verfügbar macht, werden alle öffentlichen Member des Basistyps (es sei denn, Sie sind explizit als com unsichtbar markiert, was redundant wäre) werden für com verfügbar gemacht. Wenn der Basistyp neue Member in einer nachfolgenden Version hinzufügt, werden alle com-Clients, die an die Klassen Schnittstelle des abgeleiteten Typs gebunden sind, möglicherweise nicht mehr unterbrechen. Für COM sichtbare Typen sollten nur von sichtbaren com-Typen abgeleitet werden, um die Wahrscheinlichkeit zu verringern, dass com-Clients unterbrochen werden

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die Basis Typen com sichtbar machen, oder der abgeleitete Typ com ist unsichtbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)