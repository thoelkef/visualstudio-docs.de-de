---
title: 'CA2109: Sichtbare Ereignishandler überprüfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 481f03cc9f1699a794c0f34159afd7faa6a50c3d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915065"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Sichtbare Ereignishandler überprüfen
|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt.

## <a name="rule-description"></a>Regelbeschreibung
 Eine extern sichtbare Methode für die Ereignisbehandlung präsentiert ein Sicherheitsproblem, die Überprüfung erfordert.

 Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist. Ein Ereignishandler, ein Delegattyp, der verfügbar gemachte Methode aufruft, kann zu jedem beliebigen Ereignis hinzugefügt werden, solange die Signaturen für Ereignishandler und Ereignis übereinstimmen. Ereignisse können von jedem Code ausgelöst werden und häufig von absolut vertrauenswürdigen Systemcode Reaktion auf Benutzeraktionen wie das Klicken auf eine Schaltfläche ausgelöst werden. Eine Ereignisbehandlungsmethode eine sicherheitsüberprüfung hinzugefügt wird nicht verhindert Code registrieren einen Ereignishandler, der die Methode aufruft.

 Eine Anforderung kann keine Methode aufgerufen, indem ein Ereignishandler zuverlässig geschützt werden. Security fordert Hilfe Code von nicht vertrauenswürdigen Aufrufern zu schützen, mithilfe der Aufrufer in der Aufrufliste. Code, der ein Ereignis einen Ereignishandler hinzugefügt ist nicht unbedingt in der Aufrufliste vorhanden, wenn der Ereignishandler Methoden ausführen. Aus diesem Grund die Aufrufliste möglicherweise nur hoch vertrauenswürdige Aufrufer, wenn die Ereignishandlermethode aufgerufen wird. Dies bewirkt, dass Anforderungen, die durch die Ereignishandlermethode vorgenommen wird, erfolgreich ausgeführt werden kann. Darüber hinaus kann die geforderte Berechtigung übergeben werden, wenn die Methode aufgerufen wird. Aus diesen Gründen kann das Risiko eines nicht korrigieren und einen Verstoß gegen diese Regel nur nach dem Überprüfen der Ereignisbehandlungsmethode bewertet werden. Wenn Sie den Code überprüfen, sollten Sie die folgenden Probleme:

-   Möglich Ihre Ereignishandler keine Vorgänge, die gefährliche oder ausgenutzt werden können, z. B. die Assertion der Berechtigungen oder Unterdrücken von nicht verwaltetem Code eine Berechtigung sind?

-   Was die Sicherheitsrisiken zu und von Ihrem Code sind, da es zu einem beliebigen Zeitpunkt mit nur hoch ausgeführt werden kann, vertrauenswürdige Aufrufer auf dem Stapel?

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Methode, und die folgenden ausgewertet:

-   Können Sie die Ereignisbehandlungsmethode nicht öffentlichen vornehmen?

-   Können Sie alle gefährliche Funktionen aus der Ereignishandler verschieben?

-   Wenn eine sicherheitsforderung erzwungen wird, kann dies auf eine andere Weise werden erreicht?

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer sorgfältigen sicherheitsreview, um sicherzustellen, dass Ihr Code kein Sicherheitsrisiko.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt eine Ereignisbehandlungsmethode, die durch bösartigen Code missbraucht werden kann.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
