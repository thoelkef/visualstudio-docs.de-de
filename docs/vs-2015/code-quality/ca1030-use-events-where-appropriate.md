---
title: 'CA1030: Ereignisse nach Bedarf verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544520"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name einer öffentlichen, geschützten oder privaten Methode beginnt mit einer der folgenden Methoden:

- Addon

- RemoveOn

- Fire

- Züchten

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse folgen dem Observer-oder Publish-Subscribe-Entwurfsmuster. Sie werden verwendet, wenn eine Zustandsänderung in einem Objekt an andere Objekte übermittelt werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

 Einige häufige Beispiele für Ereignisse finden Sie in Benutzeroberflächen Anwendungen, bei denen eine Benutzeraktion, wie z. b. das Klicken auf eine Schaltfläche, bewirkt, dass ein Code Ausschnitt ausgeführt wird Das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignis Modell ist nicht auf Benutzeroberflächen beschränkt. es sollte überall dort verwendet werden, wo Sie Zustandsänderungen an ein oder mehrere Objekte übermitteln müssen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn die-Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie den Entwurf für die Verwendung des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignis Modells ändern.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn die Methode nicht mit dem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Ereignis Modell funktioniert.
