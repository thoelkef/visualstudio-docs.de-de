---
title: 'CA1030: Nach Möglichkeit Ereignisse verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6d1b0bac434ad7a182dc56ac08173646068623bd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547545"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden
|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Namen einer öffentlichen, geschützten oder privaten Methode beginnt mit einer der folgenden:

- -Add-On

- RemoveOn

- Auslösen

- Auslösen

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse befolgen das Entwurfsmuster "Beobachter" oder "Veröffentlichen-Abonnieren"; Sie werden verwendet, wenn eine Zustandsänderung bei einem Objekt auf andere Objekte übertragen werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

 Einige allgemeine Beispiele für Ereignisse werden in Benutzeroberflächenanwendungen gefunden, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment des Codes dass ausgeführt. Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell ist nicht auf Benutzeroberflächen beschränkt; sie sollten überall dort verwendet werden Sie kommunizieren müssen, Zustandsänderungen auf eine oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie erwägen, den Entwurf zu verwenden, Ändern der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Eine Warnung dieser Regel zu unterdrücken, wenn die Methode funktioniert nicht mit der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Ereignismodell.