---
title: 'CA2109: Sichtbare Ereignishandler überprüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de5ab1fac368f1da1ceea39df19b198a22d999c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808288"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Sichtbare Ereignishandler überprüfen.

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt.

## <a name="rule-description"></a>Regelbeschreibung
 Eine extern sichtbare Methode für die Ereignisbehandlung stellt ein Sicherheitsproblem, das eine Überprüfung erforderlich ist.

Ereignisbehandlungsmethoden nicht verfügbar, es sei denn, absolut notwendig. Ein Ereignishandler, der ein Delegattyp, der verfügbar gemachte Methode aufruft kann zu jedem beliebigen Ereignis hinzugefügt werden, solange die Signaturen für Ereignishandler und Ereignis übereinstimmen. Ereignisse können von jedem Code ausgelöst werden und werden häufig von hochgradig vertrauenswürdigen Systemcode als Reaktion auf Benutzeraktionen wie das Klicken auf eine Schaltfläche ausgelöst. Hinzufügen eine sicherheitsüberprüfung auf eine Methode zur Verarbeitung von Ereignissen verhindert nicht Code aus der Registrierung eines ereignishandlers, das die Methode aufruft.

 Eine Anforderung kann nicht zuverlässig zu schützen eine Methode, die von einem Ereignishandler aufgerufen. Sicherheit fordert Hilfe durch Untersuchen der Aufrufer in der Aufrufliste Code aus nicht vertrauenswürdigen Aufrufern zu schützen. Code, der ein Ereignis einen Ereignishandler hinzugefügt ist nicht unbedingt in der Aufrufliste vorhanden, wenn es sich bei der Ereignishandler Methoden ausgeführt werden. Aus diesem Grund die Aufrufliste möglicherweise nur sehr vertrauenswürdige Aufrufer, wenn die Ereignishandlermethode aufgerufen wird. Dies bewirkt, dass Anforderungen, die von der Ereignishandlermethode für erfolgreich ausgeführt werden. Darüber hinaus kann die geforderte Berechtigung übergeben werden, wenn die Methode aufgerufen wird. Aus diesen Gründen kann das Risiko nicht beheben einen Verstoß gegen diese Regel nur nach dem Überprüfen der Ereignisbehandlungsmethode bewertet werden. Wenn Sie den Code überprüfen, die folgenden Punkte:

- Führt Ihr Ereignishandler alle Vorgänge, die gefährliche oder ausgenutzt werden können, z. B. berechtigungserteilung oder Unterdrücken von nicht verwaltetem Codeberechtigung sind?

- Gibt den Sicherheitsrisiken, die in und aus Ihrem Code, da es zu einem beliebigen Zeitpunkt mit hoher nur ausgeführt werden kann, vertrauenswürdige Aufrufer auf dem Stapel?

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Methode aus, und bewerten Sie die folgenden:

- Können Sie die Methode zur Verarbeitung von Ereignissen nicht öffentlichen vornehmen?

- Können Sie alle gefährlichen Funktionalität aus den Ereignishandler verschieben?

- Wenn eine sicherheitsforderung festgelegt wurde, kann dies auf andere Weise werden erreicht?

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer sorgfältigen sicherheitsreview, um sicherzustellen, dass Ihr Code kein Sicherheitsrisiko darstellt.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt eine Ereignisbehandlung-Methode, die durch bösartigen Code missbraucht werden kann.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>