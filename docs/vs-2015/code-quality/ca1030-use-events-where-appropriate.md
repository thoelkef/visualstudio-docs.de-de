---
title: 'CA1030 nach Möglichkeit: Ereignisse verwenden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590243"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1030 nach Möglichkeit: nach Möglichkeit Ereignisse verwenden](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate).

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Namen einer öffentlichen, geschützten oder privaten Methode beginnt mit einer der folgenden:

-   -Add-On

-   RemoveOn

-   Auslösen

-   Auslösen

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse befolgen das Entwurfsmuster "Beobachter" oder "Veröffentlichen-Abonnieren"; Sie werden verwendet, wenn eine Zustandsänderung bei einem Objekt auf andere Objekte übertragen werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

 Einige allgemeine Beispiele für Ereignisse werden in Benutzeroberflächenanwendungen gefunden, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment des Codes dass ausgeführt. Die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignismodell ist nicht auf Benutzeroberflächen beschränkt; sie sollten überall dort verwendet werden Sie kommunizieren müssen, Zustandsänderungen auf eine oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie erwägen, den Entwurf zu verwenden, Ändern der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignismodell.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Eine Warnung dieser Regel zu unterdrücken, wenn die Methode funktioniert nicht mit der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignismodell.



