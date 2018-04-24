---
title: 'CA1030: Nach Möglichkeit Ereignisse verwenden'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66b9893d6ad0c47dde69fa2cb6d35ee228cff59e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden
|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine öffentlich, geschützt oder privat Methodenname beginnt mit einer der folgenden:

-   AddOn

-   RemoveOn

-   Auslösen

-   Auslösen

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse folgen das Entwurfsmuster "Beobachter" oder veröffentlichen-abonnieren. Sie werden verwendet, wenn eine statusänderung in einem Objekt auf andere Objekte übertragen werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

 Einige gängige Beispiele von Ereignissen werden in Benutzeroberflächenanwendungen erörtert, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment der dass auszuführenden Code. Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell ist nicht auf Benutzeroberflächen beschränkt; er sollte überall dort verwendet werden Sie kommunizieren müssen, Zustand ändert, um ein oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie erwägen, den Entwurf zu verwenden, ändern die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Eine Warnung dieser Regel zu unterdrücken, sofern die Methode funktioniert nicht mit der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell.