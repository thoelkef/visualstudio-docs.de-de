---
title: 'CA2211: Nicht konstante Felder sollten nicht sichtbar sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 77909627385a7aa2e41f87c23ec41dc8ac0e1a5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920362"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Nicht konstante Felder sollten nicht sichtbar sein.

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentliches oder geschütztes statisches Feld ist nicht konstant und ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Der Zugriff auf ein solches Feld muss sorgfältig gesteuert werden und erfordert erweiterte Programmierverfahren für die Synchronisierung des Zugriffs auf das Klassenobjekt. Da es schwierig ist, die Kenntnisse zu erlernen und zu meistern, und das Testen eines solchen Objekts seine eigenen Herausforderungen darstellt, werden statische Felder am besten zum Speichern von Daten verwendet, die sich nicht ändern. Diese Regel gilt für Bibliotheken. Anwendungen sollten keine Felder verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, machen Sie das statische Feld konstant oder schreibgeschützt. Wenn dies nicht möglich ist, sollten Sie den Typ so umgestalten, dass er einen alternativen Mechanismus verwendet, wie z. b. eine Thread sichere Eigenschaft, die den Thread sicheren Zugriff auf das zugrunde liegende Feld verwaltet. Beachten Sie, dass Probleme, wie z. b. Sperr Konflikte und Deadlocks, die Leistung und das Verhalten der Bibliothek beeinflussen können.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie eine Anwendung entwickeln und daher die vollständige Kontrolle über den Zugriff auf den Typ haben, der das statische Feld enthält. Bibliotheks-Designer sollten eine Warnung aus dieser Regel nicht unterdrücken. durch die Verwendung nicht konstanter statischer Felder kann die Verwendung der Bibliothek für Entwickler schwierig werden.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]