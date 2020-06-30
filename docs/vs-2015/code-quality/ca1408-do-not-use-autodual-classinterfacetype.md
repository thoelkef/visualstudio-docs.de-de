---
title: 'CA1408: AutoDual classinterfaketype nicht verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534874"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType nicht verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Component Object Model sichtbarer Typ (com) ist mit dem- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribut gekennzeichnet, das auf den Wert von festgelegt ist `AutoDual` <xref:System.Runtime.InteropServices.ClassInterfaceType> .

## <a name="rule-description"></a>Beschreibung der Regel
 Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. Wenn das- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribut nicht angegeben wird, wird standardmäßig eine Dispatch-Schnittstelle verwendet.

 Sofern nicht anders gekennzeichnet, sind alle öffentlichen nicht generischen Typen für com sichtbar. alle nicht öffentlichen und generischen Typen sind für com nicht sichtbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert des <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attributs in den `None` Wert von, <xref:System.Runtime.InteropServices.ClassInterfaceType> und definieren Sie die-Schnittstelle explizit.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, es ist sicher, dass sich das Layout des Typs und der zugehörigen Basis Typen in einer zukünftigen Version nicht ändern.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt, und eine erneute Deklaration der-Klasse, um eine explizite-Schnittstelle zu verwenden.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource-Schnittstellen als IDispatch markieren.](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Weitere Informationen
 [Einführung in die Klassen Schnittstelle](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualifizieren von .NET-Typen für die Interoperation](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
