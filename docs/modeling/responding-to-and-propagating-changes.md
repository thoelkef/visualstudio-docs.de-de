---
title: Reagieren auf und Propagieren von Änderungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b35f465d9fa7683c6bc26c9c79bab478ce7ecf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939592"
---
# <a name="responding-to-and-propagating-changes"></a>Reagieren auf und Propagieren von Änderungen
Wenn ein Element erstellt, gelöscht oder aktualisiert wird, können Sie Code schreiben, die die Änderung auf andere Teile des Modells oder auf externe Ressourcen wie Dateien, Datenbanken oder andere Komponenten weitergibt.

## <a name="in-this-section"></a>In diesem Abschnitt
 Betrachten Sie als Richtwert diese Techniken in der folgenden Reihenfolge aus:

|Verfahren|Szenarien|Weitere Informationen|
|-|-|-|
|Definieren Sie eine Eigenschaft "Domain" berechnet.|Eine Eigenschaft "Domain", dessen Wert aus anderen Eigenschaften im Modell berechnet wird. Z. B. ein Preis, der die Summe der Preise verwandter Elemente ist.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|
|Definieren einer benutzerdefinierten Domäne Speichereigenschaft an.|Eine Domäneneigenschaft in anderen Teilen des Modells oder extern gespeichert. Beispielsweise könnte eine Ausdruckszeichenfolge in einer Struktur im Modell analysiert werden.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|
|Überschreiben Sie Handler für wertänderungen von z. B. "onvaluechanging" und "OnDeleting"|Halten Sie verschiedene Elemente synchron zu, und bewahren Sie externe Werte synchron mit dem Modell.<br /><br /> Schränken Sie die Werte für den definierten Bereichen.<br /><br /> Wird aufgerufen, unmittelbar vor und nach dem Eigenschaftswert und andere Änderungen. Sie können die Änderung durch Auslösen einer Ausnahme beendet.|[Handler für Wertänderungen von Domäneneigenschaften](../modeling/domain-property-value-change-handlers.md)|
|Regeln|Sie können Regeln definieren, die für die Ausführung unmittelbar vor dem Ende einer Transaktion in der Warteschlange befinden in denen eine Änderung geschehen ist. Sie werden nicht auf Rückgängig- oder Wiederholen ausgeführt. Verwenden Sie sie an, um einen Teil des Speichers mit einem anderen synchron bleiben.|[Regeln propagieren Änderungen im Modell](../modeling/rules-propagate-changes-within-the-model.md)|
|Store-Ereignisse|Die Modellierung Store bietet die Benachrichtigungen von Ereignissen, z. B. hinzufügen oder Löschen eines Elements oder der Link den Wert einer Eigenschaft ändern. Das Ereignis wird auch für rückgängig und wiederholen ausgeführt. Verwenden Sie Speicherereignisse, um Werte zu aktualisieren, die nicht im Speicher vorhanden sind.|[Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Ereignisse für .NET|Formen besitzen, Ereignishandler, die auf Mausklicks und anderen Bewegungen zu reagieren. Sie müssen für diese Ereignisse für jedes Objekt zu registrieren. Registrierung erfolgt in der Regel in einer Außerkraftsetzung der InitializeInstanceResources und muss für jedes Element ausgeführt werden.<br /><br /> Diese Ereignisse treten in der Regel außerhalb einer Transaktion.|[Vorgehensweise: Abfangen eines Klicks auf einer Form oder eines Decorator-Element](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Regeln für Grenzen|Eine begrenzungsregel wird verwendet, insbesondere, um die Grenzen einer Form zu beschränken.|[BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|Regeln für die Adressenauswahl|Auswahlregeln beschränken insbesondere an, was der Benutzer auswählen kann.|[Vorgehensweise: Zugriff auf und Einschränken der aktuellen Auswahl](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Geben Sie die Modellelemente-Zustände, die mithilfe der Features von Formen und Konnektoren, z. B. Schatten, Pfeilspitzen, Farbe, und die Linienstärke und Stil an.|[Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Vergleichen von Regeln und Store-Ereignisse**
 Änderung Notifier, Regeln und Ereignisse werden ausgeführt, wenn in einem Modell Änderungen.

 Regeln werden in der Regel angewendet, mit der Endtransaktion, in der die Änderung aufgetreten ist, und Ereignisse werden angewendet, nachdem die Änderungen in einer Transaktion ein Commit ausgeführt werden.

 Verwenden Sie Speicherereignisse, um das Modell mit Objekten außerhalb der Store, und Regeln, die Konsistenz in den Store zu synchronisieren.

-   **Erstellen benutzerdefinierter Regeln** als abgeleitete Klasse von einer abstrakten-Regel, erstellen Sie eine benutzerdefinierte Regel. Sie müssen auch das Framework über die benutzerdefinierte Regel benachrichtigen. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).

-   **Abonnieren von Ereignissen** , bevor Sie ein Ereignis abonnieren können, erstellen Sie einen Ereignishandler und Delegaten. Verwenden Sie dann die <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>Eigenschaft, um das Ereignis abonnieren. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).

-   **Änderungen werden rückgängig gemacht** Wenn Sie eine Transaktion rückgängig zu machen, werden Ereignisse ausgelöst, aber Regeln werden nicht angewendet. Wenn eine Regel wird ein Wert geändert, und Sie diese Änderung rückgängig zu machen, wird der Wert auf den ursprünglichen Wert zurückgesetzt, während die Rückgängig-Aktion. Wenn ein Ereignis ausgelöst wird, müssen Sie den Wert manuell wieder auf den ursprünglichen Wert ändern. Weitere Informationen zu Transactons und rückgängig machen, finden Sie unter [Vorgehensweise: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).

-   **Ereignisargumente, Regeln und Ereignisse übergeben** beide Ereignisse und Regeln werden übergeben, eine `EventArgs` Parameter, die Informationen dazu, wie das Modell geändert.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Abfangen eines Klicks auf einer Form oder eines Decorator-Element](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)