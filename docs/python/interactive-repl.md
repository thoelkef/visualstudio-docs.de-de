---
title: Python Interactive REPL in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: f31d92f193af3fb32f61030ca52e444ae2baa60b
ms.lasthandoff: 03/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Arbeiten mit dem interaktiven Python-Fenster

Visual Studio bietet ein interaktives „Lesen-Auswerten-Ausgeben-Schleife“-Fenster (Read Eval Print Loop, REPL) für Ihre Python-Umgebungen, das eine Verbesserung ist gegenüber dem REPL, das Sie mit der Eingabe von `python.exe` in der Befehlszeile erhalten. Im (mit den Menübefehlen **Ansicht > Weitere Fenster > Interaktives &lt;Umgebung&gt;** geöffneten) interaktiven Fenster können Sie beliebigen Python-Code eingeben und sofort Ergebnisse sehen, was Ihnen hilft, APIs kennenzulernen und mit ihnen zu experimentieren sowie interaktiven Code zu entwickeln, den Sie in Ihre Projekte einbeziehen.

![Interaktives Python-Fenster](media/interactive-window.png)

Visual Studio stellt eine Reihe von Python-REPL-Modi zur Auswahl:

| REPL | Beschreibung | Bearbeiten | Debuggen | Bilder |
| --- | --- | --- | --- | --- |
| Standard | Standard-REPL, kommuniziert direkt mit Python | Standardbearbeitung (mehrzeilig usw.). | Ja, über `$attach` | Nein |
| Debuggen | Standard-REPL, kommuniziert mit gedebuggtem Python-Prozess | Standardbearbeitung | Nur Debuggen | Nein |
| IPython | REPL kommuniziert mit IPython-Back-End | IPython-Befehle, Pylab-Vorteile | Nein | Ja, inline in REPL |
| IPython ohne Pylab | REPL kommuniziert mit IPython-Back-End | Standardmäßiges IPython | Nein | Ja, separates Fenster | 

Dieses Thema beschreibt den **Standard**- und **Debug**-REPL-Modus. Ausführliche Informationen zu den IPython-Modi finden Sie unter [Using Python in the Interactive Window](interactive-repl-ipython.md) (Verwenden von Python im interaktiven Fenster).

Eine Einführung in das interaktive Python-Fenster finden Sie unter [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Erste Schritte mit Python in Visual Studio, Teil 5: interaktives REPL) (youtube.com, 2 Min. 51 Sek.).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Öffnen eines interaktiven Fensters

Es gibt mehrere Methoden zum Öffnen des interaktiven Fensters für eine Umgebung.

Erstens: Wechseln Sie zum Python-Umgebungenfenster (**Ansicht > Weitere Fenster > Python-Umgebungen** oder STRG+K,STRG+'), und wählen Sie den Befehl **Interaktives Fenster öffnen** oder eine Schaltfläche für eine ausgewählte Umgebung.

![Link zu interaktivem Fenster in Python-Umgebungen](media/interactive-window-opening.png)

Zweitens: **Ansicht > Weitere Fenster** bietet **Interaktiv**-Befehle für jede Ihrer Umgebungen, in der Regel unten im Menü:

![Menüelemente für interaktives Fenster in „Ansicht > Weitere Fenster“](media/interactive-window-menu.png)

Drittens: Sie können in der Startdatei Ihres Projekts – oder für eine eigenständige Datei – durch Auswahl des Menübefehls **Debuggen > [Projekt | Datei] in interaktivem Python ausführen** (UMSCHALT+Alt+5) ein interaktives Fenster öffnen:

![Ausführen des Projekts im interaktiven Python-Menü](media/interactive-execute-project.png)

Schließlich können Sie Code in der Datei auswählen und den unten beschriebenen Befehl [An Interactive senden](#send-code-to-interactive) verwenden.

## <a name="interactive-window-options"></a>Optionen für das interaktive Fenster

Sie können verschiedene Aspekte des interaktiven Fensters über **Interaktives Fenster konfigurieren** im Python-Umgebungenfenster oder über **Tools > Optionen > Python-Tools > Interaktive Fenster** steuern:

![Optionen für interaktives Python-Fenster](media/interactive-window-options.png)

Beachten Sie, dass es auch einen separaten Satz von Optionen für das **Fenster zum interaktiven Debuggen** gibt, die das Verhalten bei Verwendung während einer Debugsitzung steuern:

![Debugoptionen für interaktives Python-Fenster](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>Verwenden des interaktiven Fensters

Sobald das interaktive Fenster geöffnet ist, können Sie beginnen, Zeile für Zeile Code an der `>>>`-Eingabeaufforderung einzugeben. Das interaktive Fenster führt jede Zeile nach der Eingabe aus, Importieren von Modulen, Definieren von Variablen usw. eingeschlossen. Sie können dies in den ersten beiden Zeilen in der Abbildung unten sehen:

![Interaktives Python-Fenster](media/interactive-window.png)

Eine Ausnahme ist, wenn eine Anweisung mit einem Doppelpunkt endet, wie die obige `for`-Anweisung, da das interaktive Fenster weiß, dass zusätzliche Codezeilen erforderlich sind, bevor es den Codeblock richtig ausführen kann. In diesem Fall ändert sich die Eingabeaufforderungszeile in `...`, um anzugeben, dass Sie zusätzliche Zeilen für den Block eingeben müssen, wie in der obigen Grafik in der vierten und fünften Zeile dargestellt. Wenn Sie in einer leeren Zeile die EINGABETASTE drücken, schließt das interaktive Fenster den Block und führt ihn im Interpreter aus.

> [!Tip]
> Eine Verbesserung im Vergleich zum üblichen Befehlszeilen-REPL von Python ist im interaktiven Fenster das automatische Einrücken von Anweisungen, die zum gleichen Bereich gehören. Sein Verlauf (abgerufen mit der NACH-OBEN-TASTE) bietet auch mehrzeilige Elemente, während im Befehlszeilen-REPL nur einzelne Zeilen möglich sind.

Das interaktive Fenster ist eine hervorragende Möglichkeit, eine neue Bibliothek zu testen. Sie können die Bibliothek importieren und dann die untergeordneten Pakete, Klassen und Funktionen untersuchen.  Python informiert Sie über alle diese Informationen mithilfe der `help()`-Funktion.  Darüber hinaus stellt Python in Visual Studio Vorschläge und Dokumentation auf Grundlage der im Editor verwendeten Codemodellierung bereit, ohne dass dafür die Bibliothek ausgeführt werden muss.  Wenn Sie Code ausführen, verwendet Visual Studio Informationen aus der Python-Laufzeit zur Verbesserung dieser Vorschläge.  

<a name="meta-commands"></a> Das interaktive Fenster unterstützt auch mehrere Metabefehle. Alle Metabefehle beginnen mit `$`, und Sie können `$help` eingeben, um eine Liste der Metabefehle abzurufen, und `$help <command>`, um nähere Informationen zur Verwendung eines bestimmten Befehls zu erhalten.

| Metabefehl | Beschreibung |
| --- | --- |
| `$$` | Fügt einen Kommentar ein, was das Kommentieren von Code während der gesamten Sitzung erleichtert. |
| `$attach` | Fügt den Visual Studio-Debugger dem REPL-Fensterprozess an, um das Debuggen zu aktivieren. |
| `$cls`, `$clear` | Löscht den Inhalt des Editorfensters, Verlauf und Ausführungskontext bleiben erhalten. |
| `$help` | Zeigt eine Liste von Befehlen an, oder Hilfe zu einem bestimmten Befehl. |
| `$load` | Lädt Befehle aus einer Datei und führt sie aus. |
| `$mod` | Legt das angegebene Modul als aktuellen Bereich fest. |
| `$reset` | Setzt die Ausführungsumgebung auf den ursprünglichen Zustand zurück, behält jedoch den Verlauf bei. |
| `$wait` | Wartet mindestens die angegebene Zahl von Millisekunden. |

Die Befehle sind auch über MEF (das Managed Extensibility Framework für .NET) erweiterbar.

## <a name="switching-scopes"></a>Wechseln von Bereichen

Standardmäßig wird der Bereich des interaktiven Fensters für ein Projekt auf die Startdatei des Projekts beschränkt, als ob Sie es von der Befehlszeile aus ausführen würden. Für eine eigenständige Datei ist der Bereich auf diese Datei beschränkt. Sie können jedoch während der REPL-Sitzung jederzeit im Dropdownmenü am oberen Rand des interaktiven Fensters den Bereich wechseln:

![Bereiche des interaktiven Fensters](media/interactive-scopes.png)

Sobald Sie ein Modul importieren, z.B. durch Eingabe von `import os`, sehen Sie in der Dropdownliste Optionen zum Wechsel in einen beliebigen Bereich dieses Moduls. Sie sehen im interaktiven Fenster auch eine Meldung, die den neuen Bereich angibt, damit Sie verfolgen können, wie ein bestimmter Zustand während einer Sitzung zustande gekommen ist.

Bei Eingabe von `dir()` in einem Bereich werden gültige Bezeichner in diesem Bereich einschließlich Funktionsnamen, Klassen und Variablen angezeigt. Bei Verwendung von `$mod importlib` gefolgt von `dir()` wird z.B. Folgendes angezeigt:

![Interaktives Fenster im Bereich „importlib“](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>Befehl „An Interactive senden“

Außer direkt im interaktiven Fenster zu arbeiten, können Sie im Editor Code auswählen, mit der rechten Maustaste klicken und **An Interactive senden** wählen:

![Menübefehl „An Interactive senden“](media/interactive-send-to.png)

Dies ist auch zur iterativen oder evolutionären Codeentwicklung inklusive des Testens Ihres Codes während der Entwicklung nützlich. Sobald Sie einen Codeausschnitt an das interaktive Fenster gesendet und seine Ausgabe gesehen haben, können Sie z.B. die NACH-OBEN-TASTE drücken, um den Code erneut anzuzeigen, ihn ändern und schnell testen, indem Sie STRG+EINGABETASTE drücken. (Durch Drücken der EINGABETASTE am Ende der Eingabe wird diese ausgeführt. Wenn Sie aber die EINGABETASTE in der Mitte der Eingabe drücken, wird eine neue Zeile eingefügt.) Sobald Sie den gewünschten Code haben, können Sie ihn problemlos wieder in die Projektdatei kopieren.

Sie können auch Code auswählen, mit der rechten Maustaste klicken und **An definierendes Modul senden** wählen, worauf der interaktive Prozess durchsucht wird, um das Modul zu finden, das der aktuell bearbeiteten Datei entspricht. Wenn der Befehl das richtige Modul findet, wird der `$mod`-Metabefehl verwendet, um zu diesem Modul zu wechseln (das Teil des Sitzungsverlaufs des interaktiven Fensters wird), und fügt die Auswahl zur Evaluierung in das interaktive Fenster ein. Dies kürzt den Prozess von Kopieren von Code in den Editor, Wechseln von Bereichen im interaktiven Fenster und manuellem Einfügen ab.

## <a name="intellisense-behavior"></a>IntelliSense-Verhalten

Das interaktive Fenster enthält IntelliSense auf der Basis von Liveobjekten, im Gegensatz zum Code-Editor, in dem IntelliSense nur auf der Quellcodeanalyse basiert. Dadurch sind Vorschläge im interaktiven Fenster korrekter, insbesondere bei dynamisch generiertem Code. Der Nachteil besteht darin, dass Funktionen mit Nebenwirkungen (z.B. Protokollierungsmeldungen) Ihre Entwicklungserfahrung beeinträchtigen können.

Wenn dieses Problem auftritt, ändern Sie die Einstellungen unter **Tools > Optionen > Python-Tools > Interaktive Fenster** in der Gruppe **Vervollständigungsmodus**:

- **Ausdrücke nie auswerten**: Normales IntelliSense-Modul wird für Vorschläge verwendet.
- **Ausdrücke mit Aufrufen nie auswerten** (Standard): Einfache Ausdrücke wie `a.b` werden ausgewertet, aber Ausdrücke mit Aufrufen wie z.B. `a().b` verwenden das normale Modul.
- **Ausdrücke immer auswerten**: Führt den vollständigen Ausdruck aus, um Vorschläge zu erhalten, unabhängig davon, ob Nebenwirkungen auftreten.
