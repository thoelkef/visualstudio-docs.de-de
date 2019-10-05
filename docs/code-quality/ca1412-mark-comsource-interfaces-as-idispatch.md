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
ms.openlocfilehash: caaae787d5e4801f3fc3b8d881b386595fb2eca4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234686"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren.

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ ist mit dem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> -Attribut markiert, und mindestens eine angegebene Schnittstelle ist nicht mit dem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attribut gekennzeichnet `InterfaceIsDispatch` , das auf den Wert festgelegt ist.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>wird verwendet, um die Ereignis Schnittstellen zu identifizieren, die eine Klasse für Component Object Model (com)-Clients verfügbar macht. Diese Schnittstellen müssen als `InterfaceIsIDispatch` verfügbar gemacht werden, damit Visual Basic 6 com-Clients Ereignis Benachrichtigungen empfangen können. Wenn eine Schnittstelle nicht mit dem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attribut markiert ist, wird Sie standardmäßig als duale Schnittstelle verfügbar gemacht.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie das <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> -Attribut hinzufügen oder ändern, sodass der Wert für alle Schnittstellen, die mit dem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> -Attribut angegeben werden, auf interfakeisidispatch festgelegt ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Klasse, in der eine der Schnittstellen gegen die Regel verstößt.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1408: AutoDual classinterfaketype nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch

- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)