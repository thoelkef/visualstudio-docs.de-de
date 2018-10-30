---
title: 'CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90970ca6be894719ea53ff6af725118626a52f20
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903659"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen

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

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnungen, die von dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel ist eine Methode mit markiert die <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut, und es ist ein Member einer Klasse, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut. Das sichere Attribut sollte entfernt werden.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]