---
title: 'CA1412: ComSource-Schnittstellen als IDispatch markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d72dd7e143720ce4ef2fce364a7e5ed3529ff9f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691994"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einer Klasse, in denen eine der Schnittstellen gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Auslösen von Ereignissen von einem COM-Empfänger behandelt](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [Interoperation mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
