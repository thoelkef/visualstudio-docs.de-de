---
title: "Reagieren auf und Propagieren von &#196;nderungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Ereignisse"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Reagieren auf und Propagieren von &#196;nderungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn ein Element erstellt, aktualisiert oder gelöscht wird, können Sie Code, der die Änderung in anderen Teilen des Modells weitergegeben, oder auf externe Ressourcen wie Dateien, Datenbanken oder andere Komponenten schreiben.  
  
## In diesem Abschnitt  
 Als Richtlinie sollten Sie diese Techniken in der folgenden Reihenfolge:  
  
|Technik|Szenarien|Weitere Informationen|  
|-------------|---------------|---------------------------|  
|Definieren einer berechneten Domäneneigenschaft.|Die Domäneneigenschaft, deren Wert eines anderen Eigenschaften im Modell berechnet wird.  Zum Beispiel ein Preis, der die Summe von Preisen von verwandten Elementen befindet.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|  
|Definieren Sie eine benutzerdefinierte Speicherdomäneneigenschaft.|Die Domäneneigenschaft in anderen Teilen des Modells extern oder legt diese fest.  Sie können beispielsweise eine Ausdruckszeichenfolge in eine Struktur im Modell analysieren.|[Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md)|  
|Überschreibungen den Modus für OnDeleting und wie OnValueChanging|Halten Sie verschiedene Elemente synchron, und halten Sie externe Werte konsistent mit dem Modell.<br /><br /> Schränken Sie Werte an definierten Bereichen ein.<br /><br /> Wird unmittelbar vor und nach Eigenschaftswert und ändert.  Sie können die Änderung zu beenden, indem Sie eine Ausnahme auslösen.|[Handler für Wertänderungen von Domäneneigenschaften](../modeling/domain-property-value-change-handlers.md)|  
|Regeln|Sie können Regeln definieren, die für die Ausführung direkt vor dem Ende der Transaktion in die Warteschlange gestellt werden, in der eine Änderung erfolgt ist.  Sie sind nicht auf Undo oder Redo ausgeführt.  Verwenden Sie es, um einen Teil des Arbeitsspeichers synchron zu halten mit anderen.|[Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md)|  
|Speicher\-Ereignisse|Der Modellierungs Datenspeicher stellt Benachrichtigungen über Ereignisse wie das Hinzufügen oder Löschen eines Elements oder des Links oder Ändern des Werts einer Eigenschaft.  Das Ereignis wird auch für Undo und Redo ausgeführt.  Verwenden Sie Speicher von Ereignissen, um Werte zu aktualisieren, die nicht im Speicher befinden.|[Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET\-Ereignisse|Forms verfügen über Ereignishandler, die auf Mausklicks reagiert und anderen wechselt den Stift.  Sie müssen für diese Ereignisse für jedes Objekt registrieren.  Registrierung wird in einer Überschreibung der InitializeInstanceResources in der Regel ausgeführt, und muss für jedes Element ausgeführt werden.<br /><br /> Diese Ereignisse treten normalerweise außerhalb einer Transaktion auf.|[Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Grenzen\-Regeln|Eine Grenzen die Regel ist speziell einschränken, die Begrenzungen einer Form verwendet.|[BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Auswahlregeln|Beschränken Auswahlregeln ausdrücklich ein, den der Benutzer auswählen kann.|[Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Geben Sie die Bedingungen der Modellelemente an, die Funktionen von Formen und Konnektoren wie Schatten, Pfeilspitzen, Farbe und Linienstärken und Format verwenden.|[Aktualisieren von Formen und Konnektoren zur Darstellung des Modells](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **Regeln und vergleichen Speicher\-Ereignisse**  
 Ändern Sie Melder, Regeln und Ereignisse werden ausgeführt, wenn Änderungen in einem Modell erfolgen.  
  
 Die Regeln werden normalerweise an der Transaktion zum Ende angewendet, in der die Änderung aufgetreten ist, und Ereignisse angewendet werden, nachdem Änderungen in einer Transaktion durchgeführt wurden.  
  
 Verwenden Sie Speicher, um das Modell zu Objekten außerhalb des Arbeitsspeichers zu synchronisieren und Regeln, die Konsistenz im Speicher beizubehalten.  
  
-   **Erstellen von benutzerdefinierten Regeln** erstellen Sie eine benutzerdefinierte Regel wie eine abgeleitete Klasse von einer abstrakten Regel.  Sie müssen das Framework für die benutzerdefinierte Regel auch benachrichtigen.  Weitere Informationen finden Sie unter [Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Um Ereignisse abonnieren** , bevor Sie ein Ereignis abonnieren können, einen Ereignishandler und einen Delegaten.  Verwenden Sie dann die Eigenschaft <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>, um das Ereignis zu abonnieren.  Weitere Informationen finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Änderungen werden rückgängig gemacht** , wenn Sie eine Transaktion rückgängig machen Ereignisse werden ausgelöst, sondern Regeln werden nicht übernommen.  Wenn eine Regel einen Wert ändert, und Sie diese Änderung rückgängig machen, wird der Wert als Rückgängigaktion den ursprünglichen Wert zurückgesetzt.  Wenn ein Ereignis ausgelöst wird, müssen Sie den Wert zurück auf den ursprünglichen Wert manuell ändern.  Um mehr darüber zu erfahren und transactons auf Rückgängig, finden Sie unter [Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Ereignis\-Argumente zu den Regeln und zu den** Regeln und \- Ereignissen**Ereignis übergeben** werden**,**`EventArgs` einem Parameter übergeben, das Informationen enthält darüber, wie sich das Modell geändert wurde.  
  
## Siehe auch  
 [Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)