---
title: 'CA2136: Elemente sollten keine Konflikt verursachenden Transparenz Anmerkungen aufweisen | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547692"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Transparendcynotationsschuldnotconflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Diese Regel wird ausgelöst, wenn ein Typmember mit einem <xref:System.Security> Sicherheits Attribut markiert ist, das eine andere Transparenz aufweist als das Sicherheits Attribut eines Containers des Members.

## <a name="rule-description"></a>Beschreibung der Regel
 Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen. Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind. Eine-Klasse, die mit dem-Attribut markiert ist, kann z. b <xref:System.Security.SecurityCriticalAttribute> . keine Methode enthalten, die mit dem-Attribut markiert ist <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, entfernen Sie das Sicherheits Attribut aus dem Code Element, das einen niedrigeren Gültigkeitsbereich aufweist, oder ändern Sie das zugehörige Attribut, sodass es mit dem enthaltenden Code Element identisch ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Warnungen von dieser Regel nicht unterdrücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine-Methode mit dem <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut gekennzeichnet und ist ein Member einer Klasse, die mit dem-Attribut markiert ist <xref:System.Security.SecurityCriticalAttribute> . Das Sicherheits sichere Attribut sollte entfernt werden.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
