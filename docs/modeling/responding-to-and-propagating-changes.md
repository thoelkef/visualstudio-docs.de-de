---
title: Reagieren auf und das Weitergeben von Änderungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5e0b8d90a1f062a82c80f6777d3090e8db98e5a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="responding-to-and-propagating-changes"></a>Reagieren auf und Propagieren von Änderungen
Wenn ein Element erstellt, gelöscht oder aktualisiert wird, können Sie Code schreiben, die die Änderung auf andere Teile des Modells oder auf externe Ressourcen wie Dateien, Datenbanken oder andere Komponenten weitergibt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Betrachten Sie als Richtlinie dieser Techniken in der folgenden Reihenfolge aus:  
  
|Vorgehensweise|Szenarien|Weitere Informationen|  
|---------------|---------------|--------------------------|  
|Definieren Sie eine Eigenschaft "Domain" berechnet.|Eine Eigenschaft "Domain", dessen Wert von anderen Eigenschaften im Modell berechnet wird. Beispielsweise einen Preis, der die Summe der Preise von verwandten Elementen.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|  
|Definieren einer benutzerdefinierten Domäne Speichereigenschaft an.|Eine Eigenschaft "Domain" in anderen Teilen des Modells oder extern gespeichert. Beispielsweise konnte eine Ausdruckszeichenfolge in einer Struktur in das Modell analysiert werden.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|  
|Überschreiben Sie Handler ändern, z. B. OnValueChanging und OnDeleting|Synchronisation von verschiedenen Elementen, und die Synchronisation externe Werte mit dem Modell.<br /><br /> Zu den definierten Bereichen Werte zu beschränken.<br /><br /> Wird aufgerufen, unmittelbar vor und nach dem Eigenschaftswert und anderen Änderungen. Sie können die Änderung durch Auslösen einer Ausnahme beendet.|[Handler für Wertänderungen von Domäneneigenschaften](../modeling/domain-property-value-change-handlers.md)|  
|Regeln|Sie können Regeln definieren, die für die Ausführung unmittelbar vor dem Ende einer Transaktion in der Warteschlange in denen eine Änderung durchgeführt wurde. Sie werden nicht für Rückgängigmachen oder Wiederholen ausgeführt. Verwenden Sie diese, um ein Teil des Speichers mit einem anderen synchron zu halten.|[Regeln propagieren Änderungen im Modell](../modeling/rules-propagate-changes-within-the-model.md)|  
|Speichern von Ereignissen|Die Modellierung-Store bietet die Benachrichtigungen zu Ereignisse wie das Hinzufügen oder Löschen eines Elements oder einen Link, oder Ändern des Werts einer Eigenschaft. Das Ereignis wird auch für rückgängig und wiederholen ausgeführt. Verwenden Sie Store-Ereignisse, um Werte zu aktualisieren, die nicht im Speicher vorhanden sind.|[Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Ereignisse für .NET|Formen besitzen Ereignishandler, die auf Mausklicks und andere Gesten reagieren. Sie müssen für diese Ereignisse für jedes Objekt zu registrieren. Registrierung erfolgt in der Regel in einer Überschreibung von InitializeInstanceResources und muss für jedes Element ausgeführt werden.<br /><br /> Diese Ereignisse werden in der Regel außerhalb einer Transaktion auftreten.|[Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Grenzen Regeln|Eine Regel Grenzen wird verwendet, insbesondere, um die Grenzen einer Form zu beschränken.|[BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Auswahlregeln|Auswahlregeln schränken speziell an, was der Benutzer auswählen kann.|[Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Geben Sie die Modellelemente-Zustände, die mithilfe der Funktionen von Formen und Verbindern, z. B. Schatten, Pfeilspitzen, Farbe und die Linienstärke und des Stils an.|[Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Vergleichen von Regeln und Store-Ereignisse**  
 Antragsteller ändern, Regeln und Ereignisse sind Änderungen in einem Modell führen.  
  
 Regeln werden in der Regel angewendet, auf die Endtransaktion, in der die Änderung aufgetreten ist, und Ereignisse werden angewendet, nachdem die Änderungen in einer Transaktion ein Commit ausgeführt werden.  
  
 Verwenden Sie Speicherereignisse, um das Modell mit Objekten außerhalb der Speicher und Regeln auf die Konsistenz im Speicher zu synchronisieren.  
  
-   **Erstellen benutzerdefinierter Regeln** als einer abgeleiteten Klasse eine abstrakte Regel aus, erstellen Sie eine benutzerdefinierte Regel. Sie müssen auch das Framework über die benutzerdefinierte Regel benachrichtigen. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Abonnieren von Ereignissen** , bevor Sie ein Ereignis abonnieren können, erstellen Sie ein Ereignishandler und Delegaten. Verwenden Sie dann die <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>Eigenschaft, um das Ereignis abonnieren. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Rückgängigmachen von Änderungen** Wenn Sie eine Transaktion rückgängig zu machen, werden Ereignisse ausgelöst, aber Regeln werden nicht angewendet. Wenn eine Regel einen Wert ändert ein, und Sie diese Änderung rückgängig machen, wird der Wert auf den ursprünglichen Wert zurückgesetzt, während die Rückgängig-Aktion. Wenn ein Ereignis ausgelöst wird, müssen Sie den Wert manuell wieder auf den ursprünglichen Wert ändern. Weitere Informationen zu Transactons und Rückgängigmachen finden Sie unter [wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Ereignisargumente, Regeln und Ereignisse übergeben** beide Ereignisse und Regeln werden übergeben ein `EventArgs` Parameter, der Informationen dazu, wie das Modell geändert.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Abfangen mit einem Klick auf eine Form oder einen Decorator-Element](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)