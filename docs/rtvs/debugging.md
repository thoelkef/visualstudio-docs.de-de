---
title: "Debuggen mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Debuggen von R in Visual Studio

R Tools für Visual Studio (RTVS) lässt sich mit dem vollständigen Debugvorgang von Visual Studio integrieren (siehe [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md)), einschließlich Breakpoints, Hinzufügen an laufende Prozesse, Überprüfen und Beobachten von Variablen, Überprüfen der Aufrufliste usw. Dieses Thema erforscht die Aspekte des Debuggens, die in R und RTVS exklusiv sind.

Das Starten des Debuggers für die R-Startdatei in einem R-Projekt ist dasselbe wie in anderen Projekttypen: verwenden Sie **Debuggen > Debuggen starten**, die F5-Taste oder die **Startdatei der Quelle** auf der unten dargestellten Debugsymbolleiste. Um die Startdatei zu ändern, führen Sie einen Rechtsklick auf eine Datei im Projektmappen-Explorer durch, und wählen Sie **Als R-Startskript festlegen** aus.

![Debugger-Schaltfläche „Start“ für R](~/docs/rtvs/media/debugger-start-button.png)

In jedem Fall führt das Starten des Debuggers dazu, dass die Datei im interaktiven Fenster „eingebunden“ wird, was bedeutet, dass sie dort geladen und ausgeführt wird. Wenn Sie mit dem Debuggen beginnen, werden Sie eine Ausgabe ähnlich der folgenden im interaktiven Fenster sehen:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Sie werden bemerken, dass wir die `rtvs::debug_source`-Funktion zum Einbinden des Skripts verwenden. Das ist erforderlich, da RTVS Ihren Code als Vorbereitung für das Debuggen bearbeiten muss. Wenn Sie andere RTVS-Befehle verwenden (z.B. indem Sie einen Rechtsklick auf deine Datei im Projektmappen-Explorer ausführen und den Befehl **Ausgewählte Datei(en) einbinden**), werden wir den Aufruf automatisch an `rtvs::debug_source` weiterleiten, wenn der Debugger angefügt ist.

Sie können den Debugger auch manuell direkt aus dem interaktiven Fenster mithilfe des Befehls **R Tools > Sitzung > Debugger anfügen**, des Befehls **Debuggen > An R Interactive anfügen** oder **Debugger anfügen** auf die interaktive Symbolleiste des Fensters anfügen. Sobald dies erfolgt ist, müssen Sie die Dateien einbinden, die Sie debuggen möchten. Wenn Sie die Dateien manuell einbinden möchten, stellen Sie sicher, dass Sie `rtvs::debug_source` verwenden und nicht den regulären `source`-Befehl in R. Es kann sein, dass dies in _einigen_ Fällen funktioniert, jedoch kann nicht garantiert werden, dass das Debuggen in jedem Fall funktioniert, es sei denn, Sie verwenden den `rtvs::debug_source`-Befehl.

Diese Verbindung zwischen dem Debugger und dem interaktiven Fenster vereinfacht viele Dinge, z.B. das Aufrufen (und Debuggen) einer Funktion mit unterschiedlichen Parameterwerten. Nehmen wir beispielsweise an, Sie hätten eine Funktion wie die folgende in einer eingefügten Datei (das bedeutet, dass sie in die Sitzung geladen wurde):

```R
add <- function(x, y) {
    return(x + y)
}
```

Dann legen Sie einen Haltepunkt auf der `return`-Anweisung fest. Wenn Sie nun im interaktiven Fenster `add(4,5)` eingeben, sehen Sie, dass der Debugger an Ihrem Haltepunkt anhält.


## <a name="environment-browser-in-the-interactive-window"></a>Umgebungsbrowser im interaktiven Fenster

Wenn Sie im Debugger angehalten werden, werden Sie auch bei der Aufforderung des Umgebungsbrowsers im [interaktiven Fenster](interactive-repl.md) angehalten. Diese Aufforderung erscheint als `Browse[n]>`, wobei „n“ eine Zahl darstellt.

Der Umgebungsbrowser unterstützt eine Reihe bestimmter Befehle:

| Befehl | Beschreibung | 
| --- | --- |
| n | next: führt die nächste Anweisung in der Codedatei aus (das gleiche wie „step over“) |
| s | step into: führt die nächste Anweisung in der Codedatei aus, wobei schrittweise ein Funktionsbereich ausgeführt wird, wenn die nächste Anweisung ein Funktionsaufruf ist. | 
| f | finish: führt den Rest des aktuellen Funktionsbereichs aus und wird an den Aufrufer zurückgegeben (genauso wie bei „step out“). |
| c, cont | continue: führt das Programm bis zum nächsten Haltepunkt aus. | 
| Q | quits: beendet die Debugsitzung. |
| wo | show stack: zeigt die Aufrufliste im interaktiven Fenster an. |
| help | show help: zeigt verfügbare Befehle im interaktiven Fenster an. |
| &lt;expr&gt; | evaluiert den Ausdruck in *expr*. |

![Umgebungsbrowser im interaktiven Fenster](~/docs/rtvs/media/debugger-environment-browser.png)

