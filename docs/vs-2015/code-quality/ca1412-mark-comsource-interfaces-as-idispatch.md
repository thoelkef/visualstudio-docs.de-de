---
title: 'CA1412: ComSource-Schnittstellen als IDispatch markieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 18404cf19c8ecb1554dcd14914128130ec36e366
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589565"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1412: ComSource-Schnittstellen als IDispatch markieren](https://docs.microsoft.com/visualstudio/code-quality/ca1412-mark-comsource-interfaces-as-idispatch).

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
 [Vorgehensweise: Auslösen von Ereignissen von einem COM-Empfänger behandelt](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



