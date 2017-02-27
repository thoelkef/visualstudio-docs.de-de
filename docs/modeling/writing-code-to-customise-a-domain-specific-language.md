---
title: "Schreiben von Code zum Anpassen einer dom&#228;nenspezifischen Sprache | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domain-Specific Language, Programmierung"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Schreiben von Code zum Anpassen einer dom&#228;nenspezifischen Sprache
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt wird erläutert, wie Sie benutzerdefinierten Code, um ein Modell in einer domänenspezifischen Sprache zu öffnen, zu ändern oder zu erstellen.  
  
 Es gibt mehrere Kontexte, in denen Sie Code schreiben können, der mit einem: DSL  
  
-   **Benutzerdefinierte Befehle.** Sie können einen Befehl erstellt haben, dass Benutzer aufrufen können, indem Sie im Diagramm mit der rechten Maustaste auf das Modell, und das geändert werden kann.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validierung.** Sie können Code schreiben, der überprüft, dass das Modell in einem ordnungsgemäßen Zustand befindet.  Weitere Informationen finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Das Standardverhalten überschreiben.** Sie können zahlreiche Aspekte des Codes ändern, der von DslDefinition.dsl generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Texttransformation** Textvorlagen können Sie Code schreiben, der ein Modell zugreift und eine Textdatei generiert, z. B. um Programmcode zu generieren.  Weitere Informationen finden Sie unter [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Andere Visual Studio Extensions.** Sie können separate VSIX\-Erweiterungen lesen und schreiben, die Modelle ändern.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instanzen von Klassen, die Sie in DslDefinition.dsl definieren, werden in einer Datenstruktur gespeichert, die den *Speicher* im Arbeitsspeicher *\(IMS* \) aufgerufen oder Speicher *.* Die Klassen, die Sie in einem DSL definieren, akzeptieren immer einen Speicher im Konstruktor als Argument.  Wenn z. B. das DSL Example eine Klasse definiert wird:  
  
 `Example element = new Example (theStore);`  
  
 Das Ablegen von Objekten im Speicher \(und nicht nur als gewöhnliche Objekte\) bietet mehrere Vorteile.  
  
-   **Transaktionen**.  Sie können mehrere verwandte Änderungen in einer Transaktion gruppieren:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Wenn eine Ausnahme auftritt, damit Änderungen bei der endgültigen Commit\(\) nicht ausgeführt wird, wird der Speicher auf ihren vorherigen Zustand zurückgesetzt.  Dies hilft Ihnen, um sicherzustellen, dass keine Fehler in einem inkonsistenten Zustand des Modells lassen.  Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Binäre Beziehungen**.  Wenn Sie eine Beziehung zwischen zwei Klassen definieren, können Instanzen an beiden Enden eine Eigenschaft, die zum anderen Ende navigiert.  Die beiden Enden jedes Mal synchronisiert werden.  Wenn Sie beispielsweise ein Elternschafts\-Verhältnis Rollen definieren, die Parents und untergeordnete Elemente benannt werden, könnten Sie schreiben:  
  
     `John.Children.Add(Mary)`  
  
     Beide folgenden Ausdrücke sind jetzt aus:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Sie können auch die gleiche Wirkung erzielen, indem Sie geschrieben haben:  
  
     `Mary.Parents.Add(John)`  
  
     Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Regeln und Ereignisse**.  Sie können Regeln definieren, die ausgelöst werden, wenn bestimmte Änderungen vorgenommen werden.  Die Regeln werden verwendet, z. B. Formen im Diagramm auf dem neuesten Stand bleiben mit Modellelementen, die sie selbst darstellen.  Weitere Informationen finden Sie unter [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Serialisierung**.  Der Speicher stellt eine standardmäßige Methode, die Objekte zu serialisieren, die sie in eine Datei.  Sie können die Regeln für das Serialisieren und Deserialisieren anpassen.  Weitere Informationen finden Sie unter [Anpassen von Dateispeicher und XML\-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## Siehe auch  
 [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)