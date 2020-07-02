---
title: 'CA1713: Ereignisse sollten kein Before-oder After-Präfix aufweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b05c39a9d8a4a004359baf63919eb427c25fa5d9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543961"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Ereignisse sollten kein Before- oder After-Präfix aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Ereignisses beginnt mit ' before ' oder ' After '.

## <a name="rule-description"></a>Beschreibung der Regel
 Ereignis Namen sollten die Aktion beschreiben, durch die das Ereignis ausgelöst wird. Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben. Wenn Sie z. b. ein Ereignispaar benennen, das beim Schließen einer Ressource ausgelöst wird, können Sie es als "Closing" und "Closed" anstelle von "BeforeClose" und "AfterClose" benennen.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie das Präfix aus dem Ereignis Namen, und ändern Sie ggf. den Namen so, dass er das vorhanden sein oder den letzten verstrichen eines Verbs verwendet

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.
