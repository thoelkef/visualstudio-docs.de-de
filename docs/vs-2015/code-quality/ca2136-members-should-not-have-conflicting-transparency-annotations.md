---
title: 'CA2136: Member dürfen keine in Konflikt stehenden transparenzanmerkungen aufweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b18ee5c048b0214779cdbe2635f5b7a14db8c28e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955793"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Diese Regel wird ausgelöst, wenn Sie ein Typmember mit markiert ist eine <xref:System.Security> Security-Attribut, das eine andere als das Sicherheitsattribut eines Containers von der Members Transparenz.

## <a name="rule-description"></a>Regelbeschreibung
 Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen. Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind. Z. B. eine Klasse, die mit der <xref:System.Security.SecurityCriticalAttribute> -Attribut kann keine Methode, die mit markierten enthalten die <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, entfernen Sie das Sicherheitsattribut aus dem Codeelement, das niedrigeren Bereich aufweist, oder ändern Sie das Attribut, damit das enthaltende Codeelement identisch sein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnungen, die von dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel ist eine Methode mit markiert die <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut, und es ist ein Member einer Klasse, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut. Das sichere Attribut sollte entfernt werden.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
