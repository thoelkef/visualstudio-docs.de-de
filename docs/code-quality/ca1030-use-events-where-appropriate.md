---
title: 'CA1030: NACH MÖGLICHKEIT Verwenden Sie Ereignisse'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 445330d654e870fe12aa2ca19626377972235eac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860805"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: NACH MÖGLICHKEIT Verwenden Sie Ereignisse

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

 Einige allgemeine Beispiele für Ereignisse werden in Benutzeroberflächenanwendungen gefunden, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment des Codes dass ausgeführt. Das Ereignismodell für die .NET Framework ist nicht auf Benutzeroberflächen beschränkt; Sie sollten überall dort verwendet werden, mit denen Sie kommunizieren müssen, dass Zustandsänderungen auf eine oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie den Entwurf zu verwenden, das .NET Framework-Ereignismodell ändern.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode nicht mit dem .NET Framework-Ereignismodell funktioniert.