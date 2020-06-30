---
title: 'CA2123: Überschreibungs Link Aufrufe sollten mit Base | identisch sein. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a722eb95561a1a81b0d17b8876df8b4bac048b5c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544260"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ überschreibt eine Methode oder implementiert eine Schnittstelle und hat [nicht dieselben](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) Verknüpfungs Aufrufe wie die Schnittstelle oder virtuelle Methode.

## <a name="rule-description"></a>Beschreibung der Regel
 Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Eine Verletzung wird gemeldet, wenn entweder die-Methode oder die-Basis Methode über einen Link Aufruf und das andere nicht.

 Wenn gegen diese Regel verstoßen wird, kann ein böswilliger Aufrufer den Link Aufruf nur durch Aufrufen der ungesicherten Methode umgehen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie denselben Link Aufruf auf die override aufgenommen-Methode oder-Implementierung an. Wenn dies nicht möglich ist, markieren Sie die Methode mit einer vollständigen Anforderung, oder entfernen Sie das Attribut ganz.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt verschiedene Verstöße gegen diese Regel.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 Verknüpfungs [Anforderungen](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) für [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
