---
title: Anpassen einer domänenspezifischen Sprache
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7fd63546f7d85ddbcc7661ac600a56bd340e6ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965225"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Schreiben von Code zum Anpassen einer domänenspezifischen Sprache

In diesem Abschnitt wird gezeigt, wie Sie benutzerdefinierten Code zugreifen, ändern oder erstellen Sie ein Modell in einer domänenspezifischen Sprache.

Es gibt mehrere Kontexte, in denen Sie Code schreiben können, die mit einem DSL funktioniert:

-   **Benutzerdefinierte Befehle.** Sie können einen Befehl erstellen, Benutzer können aufrufen, indem Sie mit der rechten Maustaste auf das Diagramm, und die können das Modell ändern. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

-   **Prüfung** Sie können Code schreiben, die überprüft, ob das Modell im richtigen Zustand ist. Weitere Informationen finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

-   **Überschreiben des Standardverhaltens.** Sie können zahlreiche Aspekte des Codes ändern, die von DslDefinition.dsl generiert wird. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).

-   **TextTransformation.** Sie können Textvorlagen schreiben, die Code, die greift auf ein Modell und generiert eine Textdatei, z. B. enthalten um Programmcode zu generieren. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

-   **Andere Visual Studio-Erweiterungen.** Sie können separate VSIX-Erweiterungen schreiben, die Lese- und Änderungszugriff Modelle. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Modell aus der Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Instanzen der Klassen, die Sie in DslDefinition.dsl definieren bleiben in einer Datenstruktur wird aufgerufen, die *speicherinterner Datenspeicher* (IMS) oder *Store*. Die Klassen, mit denen, die Sie immer in eine DSL definieren, nehmen einen Speicher als Argument an dem Konstruktor übergibt. Angenommen, eine Klasse, die aufgerufen wird, der DSL definiert:

`Example element = new Example (theStore);`

Beibehalten von Objekten im Speicher (statt lediglich als gewöhnliche Objekte) bietet verschiedene Vorteile.

-   **Transaktionen**. Sie können eine Reihe von zugehörigen Änderungen in einer Transaktion gruppieren:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Tritt eine Ausnahme bei der Änderung, damit die endgültige Commit() nicht ausgeführt wird, wird der Speicher auf den ursprünglichen Zustand zurückgesetzt. Dadurch können Sie sicherstellen, dass Fehler nicht das Modell in einem inkonsistenten Zustand verlassen. Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Binäre Beziehungen**. Wenn Sie eine Beziehung zwischen zwei Klassen definieren, verfügen über Instanzen an beiden Enden auf eine Eigenschaft, die navigiert zum anderen Ende aus. Die zwei Enden, sind immer synchronisiert. Beispielsweise konnten, wenn Sie eine Beziehung Personenstand mit Rollen, die mit dem Namen übergeordnete und untergeordnete Elemente definieren, Sie schreiben:

     `John.Children.Add(Mary)`

     Beide der folgenden Ausdrücke sind jetzt erfüllt:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Sie können auch durch Schreiben von unterbinden:

     `Mary.Parents.Add(John)`

     Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Regeln und Ereignisse**. Sie können Regeln definieren, die ausgelöst werden, wenn die angegebene Änderungen vorgenommen werden. Regeln werden z. B. verwendet, um die Formen im Diagramm auf dem neuesten Stand mit den Modellelementen beibehalten, die sie darstellen. Weitere Informationen finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).

-   **Serialisierung**. Der Speicher bietet ein gängiges Verfahren, um die Objekte zu serialisieren, die sie in eine Datei enthält. Sie können die Regeln für die Serialisierung und Deserialisierung anpassen. Weitere Informationen finden Sie unter [Dateispeicher anpassen und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Siehe auch

- [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)