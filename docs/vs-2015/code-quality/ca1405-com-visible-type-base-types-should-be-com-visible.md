---
title: 'CA1405: für COM sichtbare typbasistypen sollten com-sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 13a6f80bb0500286dd44e9c5ca9378e95d4b891d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661304"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Dependsonfix|

## <a name="cause"></a>Ursache
 Ein Component Object Model sichtbarer Typ (com) ist von einem Typ abgeleitet, der nicht für com sichtbar ist.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein durch COM sichtbarer Typ Elemente in einer neuen Version hinzufügt, muss er strenge Richtlinien einhalten, um zu vermeiden, dass com-Clients, die an die aktuelle Version gebunden sind, unterbrochen werden Ein Typ, der für COM unsichtbar ist, setzt voraus, dass er diese com-Versions Regeln beim Hinzufügen neuer Member nicht befolgt. Wenn ein für COM sichtbarer Typ jedoch vom COM-unsichtbar-Typ abgeleitet ist und eine Klassen Schnittstelle von <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ClassInterfaceType> (Standard) verfügbar macht, werden alle öffentlichen Member des Basistyps (es sei denn, Sie sind explizit als com unsichtbar gekennzeichnet, was redundant wäre) KOM. Wenn der Basistyp neue Member in einer nachfolgenden Version hinzufügt, werden alle com-Clients, die an die Klassen Schnittstelle des abgeleiteten Typs gebunden sind, möglicherweise nicht mehr unterbrechen. Für COM sichtbare Typen sollten nur von sichtbaren com-Typen abgeleitet werden, um die Wahrscheinlichkeit zu verringern, dass com-Clients unterbrochen werden

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die Basis Typen com sichtbar machen, oder der abgeleitete Typ com ist unsichtbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Einführung in die Klassen Schnittstellen](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [Interaktion mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
