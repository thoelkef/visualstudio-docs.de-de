---
title: 'CA1412: ComSource-Schnittstellen als IDispatch markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e0a7214ce37aa48d69b9261d686960fa0a4c308c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918643"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren.

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ist ein Typ mit markiert die <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> -Attribut und mindestens eine angegebene Schnittstelle ist nicht mit markiert die <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attributsatz auf die `InterfaceIsDispatch` Wert.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> wird verwendet, die Ereignisschnittstellen zu identifizieren, die eine Klasse, die den Component Object Model (COM)-Clients verfügbar macht. Diese Schnittstellen müssen verfügbar gemacht werden, als `InterfaceIsIDispatch` Visual Basic 6-COM-Clients, ereignisbenachrichtigungen empfangen werden können. Standardmäßig, wenn eine Schnittstelle nicht gekennzeichnet ist die <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attribut, es wird als eine duale Schnittstelle verfügbar gemacht.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, hinzufügen oder Ändern der <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> Attribut, damit der Wert auf InterfaceIsIDispatch für alle Schnittstellen festgelegt ist, die mit angegeben sind die <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einer Klasse, in denen eine der Schnittstellen gegen die Regel verstößt.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)