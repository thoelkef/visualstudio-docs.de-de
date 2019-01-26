---
title: 'CA1030: Nach Möglichkeit Ereignisse verwenden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89ee195da621ea9d7342302efadf582e21f7e619
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956726"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden.

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Namen einer öffentlichen, geschützten oder privaten Methode beginnt mit einer der folgenden:

- AddOn

- RemoveOn

- Auslösen

- Auslösen

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse befolgen das Entwurfsmuster "Beobachter" oder "Veröffentlichen-Abonnieren"; Sie werden verwendet, wenn eine Zustandsänderung bei einem Objekt auf andere Objekte übertragen werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

 Einige allgemeine Beispiele für Ereignisse werden in Benutzeroberflächenanwendungen gefunden, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment des Codes dass ausgeführt. Das Ereignismodell für die .NET Framework ist nicht auf Benutzeroberflächen beschränkt; Sie sollten überall dort verwendet werden, mit denen Sie kommunizieren müssen, dass Zustandsänderungen auf eine oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie den Entwurf zu verwenden, das .NET Framework-Ereignismodell ändern.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode nicht mit dem .NET Framework-Ereignismodell funktioniert.