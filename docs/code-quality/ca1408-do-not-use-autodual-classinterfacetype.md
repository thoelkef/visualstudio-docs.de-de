---
title: 'CA1408: AutoDual ClassInterfaceType nicht verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f324eee1ae71f063ddd19d5a7f3d82af6f45c00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType nicht verwenden
|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein sichtbar Component Object Model (COM)-Typ ist markiert, mit der <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attributsatz zur der `AutoDual` Wert <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Regelbeschreibung
 Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. In der Standardeinstellung Wenn die <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribut nicht angegeben ist, wird eine Dispatch beschränkte Schnittstelle verwendet.

 Sofern nicht anders markiert ist, sind alle öffentliche, nicht generische Typen für COM sichtbar. alle nicht öffentliche und generischen Typen sind nicht für COM sichtbar

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert von der <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attribut auf die `None` Wert <xref:System.Runtime.InteropServices.ClassInterfaceType> und definieren Sie explizit die Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, es sicher ist, dass das Layout des Typs und dessen Basistypen in einer zukünftigen Version nicht geändert werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die die Regel und eine erneute Deklaration der Klasse, um eine explizite Schnittstelle verwenden verletzt.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource-Schnittstellen als IDispatch markieren](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Siehe auch
 [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)