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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5685ad7a760e00392b5f9684cdf399ee320d4a0c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540256"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource-Schnittstellen als IDispatch markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ ist mit dem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> -Attribut markiert, und mindestens eine angegebene Schnittstelle ist nicht mit dem- <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> Attribut gekennzeichnet, das auf den Wert festgelegt ist `InterfaceIsDispatch` .

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>wird verwendet, um die Ereignis Schnittstellen zu identifizieren, die eine Klasse für Component Object Model (com)-Clients verfügbar macht. Diese Schnittstellen müssen als verfügbar gemacht werden `InterfaceIsIDispatch` , damit Visual Basic 6 com-Clients Ereignis Benachrichtigungen empfangen können. Wenn eine Schnittstelle nicht mit dem-Attribut markiert ist <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> , wird Sie standardmäßig als duale Schnittstelle verfügbar gemacht.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie das-Attribut hinzufügen oder ändern, <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> sodass der Wert für alle Schnittstellen, die mit dem-Attribut angegeben werden, auf interfakeisidispatch festgelegt ist <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, in der eine der Schnittstellen gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1408: AutoDual ClassInterfaceType nicht verwenden.](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Weitere Informationen
 Gewusst [wie: Ausführen von Ereignissen, die von einer com-Senke behandelt werden](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) , Interoperabilität [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
