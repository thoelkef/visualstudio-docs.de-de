---
title: Anpassen einer domänenspezifischen Sprache
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e62fa58d3f0678c8784cb8584a95d8475238ce0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945439"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Schreiben von Code zum Anpassen einer domänenspezifischen Sprache

In diesem Abschnitt erfahren Sie, wie Sie mit benutzerdefinierten Code zugreifen, ändern oder erstellen ein Modell in einer domänenspezifischen Sprache.

Es gibt mehrere Kontexte, in denen Sie Code schreiben können, die mit einer DSL funktioniert:

- **Benutzerdefinierte Befehle.** Sie können einen Befehl erstellen, dass Benutzer aufrufen können, indem Sie mit der rechten Maustaste auf das Diagramm, und die können das Modell zu ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Prüfung** Sie können Code schreiben, die überprüft, ob das Modell im richtigen Zustand ist. Weitere Informationen finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

- **Überschreiben des Standardverhaltens.** Sie können viele Aspekte des Codes ändern, die von "DslDefinition.DSL" generiert wird. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).

- **TextTransformation.** Sie können Textvorlagen schreiben, die Code, die ein Modell und generiert eine Textdatei, z. B. enthalten um Programmcode generieren. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

- **Andere Visual Studio-Erweiterungen.** Sie können die separate VSIX-Erweiterungen schreiben, die gelesen und Modelle zu ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Instanzen der Klassen, die Sie in "DslDefinition.DSL" definieren, befinden sich in einer Datenstruktur, die Namen der *In-Memory-Store* (IMS) oder *Store*. Die Klassen, die Sie in einer DSL, immer definieren nehmen einen Store als Argument an dem Konstruktor. Wenn beispielsweise Ihre DSL auf eine Klasse namens Beispiel definiert:

`Example element = new Example (theStore);`

Beibehalten von Objekten in den Store (statt nur als gewöhnliche Objekte) bietet mehrere Vorteile.

- **Transaktionen**. Sie können eine Reihe von aufeinander bezogene Änderungen in einer Transaktion gruppieren:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Tritt eine Ausnahme während die Änderungen, damit die endgültige Commit() nicht ausgeführt wird, wird der Store den ursprünglichen Zustand zurückgesetzt. Dadurch können Sie sicherstellen, dass Fehler nicht das Modell in einem inkonsistenten Zustand verfügbar ist. Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Binäre Beziehungen**. Wenn Sie eine Beziehung zwischen zwei Klassen definieren, müssen Instanzen an beiden Enden eine Eigenschaft, die zu der anderen Seite navigiert. Die beiden Enden, sind immer synchronisiert. Z. B. Wenn Sie eine Beziehung Personenstand mit Rollen, die mit dem Namen, übergeordneten und untergeordneten Elemente definieren, könnten Sie schreiben:

     `John.Children.Add(Mary)`

     Beide der folgenden Ausdrücke sind jetzt "true":

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Sie können auch denselben Effekt erzielen Sie durch Schreiben:

     `Mary.Parents.Add(John)`

     Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Regeln und Ereignisse**. Sie können Regeln definieren, die ausgelöst werden, wenn die angegebene Änderungen vorgenommen werden. Regeln werden z. B. verwendet, um Formen im Diagramm auf dem neuesten Stand mit den Modellelementen zu bewahren, sie stellen. Weitere Informationen finden Sie unter [reagieren auf und propagieren Änderungen](../modeling/responding-to-and-propagating-changes.md).

- **Serialisierung**. Der Store bietet eine standardisierte Möglichkeit der Objekte zu serialisieren, die sie in eine Datei enthält. Sie können die Regeln für die Serialisierung und Deserialisierung anpassen. Weitere Informationen finden Sie unter [Anpassen von Dateispeicher und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Siehe auch

- [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)