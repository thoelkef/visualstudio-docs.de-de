---
title: 'CA1408: AutoDual ClassInterfaceType nicht verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c811c7e2b6ba06c716179469c8b038fd26b3b38a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546032"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType nicht verwenden.

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Component Object Model (COM) sichtbarer Typ ist mit markiert die <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attributsatz auf die `AutoDual` Wert <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Regelbeschreibung
 Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. In der Standardeinstellung Wenn die <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribut nicht angegeben wird, eine nur-Dispatch-Schnittstelle wird verwendet.

 Sofern nicht anders markiert ist, werden alle öffentliche nicht generische Typen für COM sichtbar; alle nicht öffentliche und generische Typen sind für COM nicht sichtbar

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert von der <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attribut auf die `None` Wert <xref:System.Runtime.InteropServices.ClassInterfaceType> und definieren Sie explizit die Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nicht, es sei denn, es sicher ist, dass das Layout des Typs und dessen Basistypen in einer zukünftigen Version nicht geändert werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel und eine erneute Deklaration der Klasse, um eine explizite Schnittstelle verwenden.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource-Schnittstellen als IDispatch markieren](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Siehe auch

- [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)