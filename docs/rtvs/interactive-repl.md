---
title: "Interactive REPL mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45d7c6ff-abd3-42a4-8376-0e9c8f7226d5
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 50d5a1e4ae1eaf5bd680a1709876962feeeb3548
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="working-with-the-r-interactive-window"></a>Arbeiten mit dem interaktiven R-Fenster

R Tools für Visual Studio (RTVS) stellt ein interaktives R-Fenster bereit, das auch als **REPL**-Fenster (Read-Evaluate-Print-Loop, „Lesen-Auswerten-Ausgeben“-Schleife) bekannt ist, in das Sie R-Code eingeben und sofort die Ergebnisse sehen können. Alle Module, Syntax und Variablen sowie IntelliSense sind im interaktiven Fenster verfügbar.

Das interaktive Fenster ist auch in den regulären Editorfenstern von R enthalten. Sie können Code auswählen und STRG+EINGABE drücken oder einen Rechtsklick ausführen und **Interaktiv ausführen** auswählen, und der Code wird Zeile für Zeile im interaktiven Fenster ausgeführt, so als ob Sie ihn direkt eingeben würden. Wenn sich der Cursor auf einer einzelnen Zeile in einem Editorfenster befindet, wird durch STRG+EINGABE diese Zeile an das interaktive Fenster gesendet und bewegt den Cursor dann in die nächste Zeile. So können Sie einfach mehrfach STRG+EINGABE drücken, um durch den Code zu gehen.

Um mit diesen Features vertraut zu werden, befolgen Sie die exemplarische Vorgehensweise [Getting Started with R (Erste Schritte mit R)](getting-started-with-r.md), sowie die folgenden Abschnitte:

- [Arbeiten mit dem interaktiven Python-Fenster](#overview-of-the-interactive-window)
- [Arbeitsbereiche und Sitzungen](#workspaces-and-sessions)
- [Arbeitsverzeichnis](#working-directory)
- [Versionsgeschichte](#history)

[Codeausschnitte](code-snippets.md) funktionieren auch im interaktiven Fenster wie in R-Editorfenstern.

## <a name="overview-of-the-interactive-window"></a>Übersicht über das interaktive Fenster

Durch das Eingeben von gültigem R-Code und das Drücken der EINGABETASTE am Ende der Zeile wird der Code in dieser Zeile ausgeführt:

```
> 3 + 3
[1] 6
```

Wenn Sie die ENTERTASTE beliebig auf einer Zeile drücken, führt die Eingabe auch diese Zeile aus.

Die vorherige Eingabe und Ausgabe im REPL ist schreibgeschützt und kann nicht geändert werden. Jedoch können Sie jederzeit Text aus dem Fenster auswählen und kopieren sowie einfügen. Eingefügter Code wird so ausgeführt, als würde er Zeile für Zeile eingefügt werden.

Das heißt, wenn Sie beginnen, eine Anweisung zu tippen und die EINGABETASTE zu drücken, weiß RTVS, wann die Anweisung fortgesetzt werden muss und gibt links mit dem passenden Einzug den Mehrzeilenmodus mit der a+-Aufforderung ein. RTVS schließt auch runde Klammern, eckige Klammern und geschweifte Klammern:

![Mehrzeiliger Anweisungseintrag im interaktiven Fenster](media/repl-multiline-entry.png)

In diesem Mehrzeilenmodus führt die EINGABETASTE den Codeblock nur aus, wenn dieser am Ende des Blocks positioniert wird und fügt andernfalls eine neue Zeile ein. Sie können jedoch STRG+EINGABE an jeder beliebigen Position drücken, um den Codeblock sofort auszuführen.

### <a name="toolbar-commands"></a>Symbolleistenbefehle

Hier sehen Sie das interaktive Fenster mit seiner Symbolleiste:

![Interaktives Fenster mit Symbolleiste](media/repl-window.png)

Die meisten Symbolleistenbefehle, die unten aufgeführt sind, haben Tastaturentsprechungen und sind auch in den Menüs **R Tools > Sitzungen** und **R Tools > Arbeitsverzeichnis** (oder wie aufgeführt) verfügbar:

| Schaltfläche | Befehl | Tastenkombination | Beschreibung | 
| --- | --- | --- | --- |
| ![Schaltfläche „Zurücksetzen“](media/repl-toolbar-01-reset.png) | Zurücksetzen | Ctrl+Shift+F10 | Setzt die Sitzung des interaktiven Fensters zurück und löscht alle Variablen sowie die Versionsgeschichte. |
| ![Schaltfläche „Löschen“](media/repl-toolbar-02-clear.png) | Clear | STRG+L | Löscht die Ausgabe, die im interaktiven Fenster angezeigt wird. Beeinträchtigt keine Sitzungsvariablen oder die Versionsgeschichte. |
| ![Schaltflächen zur Versionsgeschichte](media/repl-toolbar-03-history.png) | Vorheriger History-Befehl<br/>Nächster History-Befehl | Nach oben, nach unten<br/>ALT+BILD-AUF, ALT+BILD-AB | Führt einen Bildlauf durch die Versionsgeschichte mit bestimmten Verhalten für mehrzeilige Codeblöcke aus. Weitere Informationen finden Sie unter [Versionsgeschichte](#history). |
| ![Schaltfläche „Arbeitsbereich laden“](media/repl-toolbar-04-load-workspace.png) | Arbeitsbereich laden | n/v | Lädt einen zuvor gespeicherten Arbeitsbereich (siehe [Arbeitsbereiche und Sitzungen](#workspaces-and-sessions)). |
| ![Schaltfläche „Arbeitsbereich speichern unter“](media/repl-toolbar-05-save-workspace-as.png)| Arbeitsbereich speichern unter | n/v | Speichert den aktuellen Zustand der Sitzung als Arbeitsbereich (siehe [Arbeitsbereiche und Sitzungen](#workspaces-and-sessions)). |
| ![Schaltfläche „R-Skript einbinden“](media/repl-toolbar-06-source-r-script.png) | R-Skript einbinden | STRG+UMSCHALT+S | Ruft `source` mit dem derzeit aktiven R-Skript im Visual Studio-Editor, das den Code ausführt.  Diese Schaltfläche wird nur angezeigt, wenn eine R-Datei im Visual Studio-Editor geöffnet ist. | 
| ![Schaltfläche „R-Skript mit Echo einbinden“](media/repl-toolbar-07-source-r-script-with-echo.png) | R-Skript mit Echo einbinden | STRG+UMSCHALT+EINGABETASTE | Das gleiche wie „R-Skript einbinden“, es wird jedoch der Inhalt des Skripts im interaktiven Fenster angezeigt. | 
| ![Schaltfläche „Interrupt-R“](media/repl-toolbar-08-interrupt-r.png)| Interrupt-R | Esc | Hält den ausgeführten Code im interaktiven Fenster an, so wie die `while`-Schleife, die im Screenshot am Anfang dieses Abschnitts dargestellt wird. |
| ![Schaltfläche „Debugger anfügen“](media/repl-toolbar-09b-attach-debugger.png)| Debugger anfügen | n/v | Auch mithilfe des Befehls **Debuggen > An R Interactive anfügen** verfügbar. | 
| ![Schaltfläche „Arbeitsverzeichnis auf Quelldateispeicherort festlegen“](media/repl-toolbar-10-set-working-directory-source.png)| Arbeitsverzeichnis auf Quelldateispeicherort festlegen | Strg+Umschalt+E | Legt das Arbeitsverzeichnis auf die zuletzt eingebundene Datei fest, die in das interaktive Fenster geladen wurde (mithilfe von `source`). Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |
| ![Schaltfläche „Arbeitsverzeichnis auf Projektspeicherort festlegen“](media/repl-toolbar-11-set-working-directory-to-project.png) | Arbeitsverzeichnis auf Projektspeicherort festlegen | STRG+UMSCHALTTASTE+P | Legt das Arbeitsverzeichnis auf den Stamm des zuletzt geladenen Projekts in Visual Studio fest. Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |
| (Textfeld) | Arbeitsverzeichnis auswählen | n/v | Direktes Eingabefeld für das Arbeitsverzeichnis. Weitere Informationen finden Sie unter [Arbeitsverzeichnis](#working-directory). |


## <a name="workspaces-and-sessions"></a>Arbeitsbereiche und Sitzungen

Das Ausführen von Code im interaktiven Fenster erstellt einen Kontext in Ihrer aktuellen Sitzung. Der Kontext besteht aus globalen Variablen, Funktionsdefinitionen, geladenen Bibliotheken usw. Dieser Kontext wird im Allgemeinen als *Arbeitsbereich* bezeichnen. Sie können Arbeitsbereiche jederzeit speichern und laden. 

Wenn Sie die Schaltfläche **Arbeitsbereich speichern unter** auswählen oder den Befehl **R Tools > Sitzung > Arbeitsbereich speichern unter...** verwenden, werden Sie zur Eingabe eines Speicherorts und eines Dateinamens aufgefordert (die Standarderweiterung ist `.RData`).

Um einen Arbeitsbereich mithilfe eines bestimmten Dateinamens (standardmäßig `.RData`) zu speichern, klicken Sie auf die Schaltfläche „Arbeitsbereich speichern“ in der REPL:

Um einen kürzlich gespeicherten Arbeitsbereich zu laden, klicken Sie auf die Schaltfläche **Arbeitsbereich laden**, oder verwenden Sie **R Tools > Sitzung > Arbeitsbereich laden...**, und navigieren Sie zur Arbeitsbereichdatei.

Mithilfe der Schaltfläche **Zurücksetzen** oder **R Tools > Sitzung > Zurücksetzen** können Sie den Sitzungskontext löschen. Wenn Sie eine Remotesitzung verwenden, wird beim Zurücksetzen auch das Benutzerprofil auf dem Remotecomputer gelöscht, damit alle darin gespeicherten Dateien gelöscht werden. (Siehe [Arbeitsbereiche](workspaces.md#directories-on-local-and-remote-computers).)


## <a name="working-directory"></a>Arbeitsverzeichnis

Entwickler möchten häufig ihr Arbeitsverzeichnis ändern, während sie sich in einer interaktiven Sitzung befinden. Mithilfe verschiedener Befehle, die auf der Symbolleiste zur Verfügung stehen, sowie mit dem Menü **R Tools > Arbeitsverzeichnis** und dem Kontextmenü „Projekt“ können Sie einfach ein Arbeitsverzeichnis am Speicherort einer Quelldatei, am Speicherort Ihres Projekts oder an jedem anderen beliebigen Speicherort erstellen. Damit müssen Sie nicht länger vollständige Pfadnamen oder lange relative Pfadnamen eingeben, wenn Sie sich auf Dateien beziehen.

 
## <a name="history"></a>Versionsgeschichte

Jede Zeile, die Sie im interaktiven Fenster eingeben, enthält von einem Editor gesendete Zeilen, die in der REPL-Versionsgeschichte gespeichert sind. Sie können mit den NACH-OBEN- und NACH-UNTEN-TASTEN durch die Versionsgeschichte navigieren, wie sie es wahrscheinlich von der Befehlszeile kennen.

Ein Unterschied ist, dass, wenn Sie beginnen, etwas in der aktuellen Zeile einzugeben und dann auf die NACH-OBEN-TASTE drücken, die aktuelle Zeile in Ihrer Versionsgeschichte gespeichert wird, auch wenn Sie diese Zeile noch nicht ausgeführt haben.

Die Versionsgeschichte im interaktiven Fenster arbeitet intelligent mit den Anweisungen eines anderen mehrzeiligen Codeblocks zusammen. Wenn Sie mithilfe der NACH-OBEN- und NACH-UNTEN-TASTEN durch die Versionsgeschichte browsen, werden mehrzeilige Codeblöcke als ganze Einheit abgerufen und als aktueller Eintrag dargestellt. Zu diesem Zeitpunkt navigieren die Pfeiltasten Zeile für Zeile durch den Codeblock, bis das obere oder untere Ende erreicht ist. Am oberen Rand des Codeblocks ruft die NACH-OBEN-TASTE das vorherige Element in der Versionsgeschichte ab. Am unteren Rand ruft die NACH-UNTEN-TASTE das nächste Element ab.

Durch dieses Verhalten erfolgt eine Anpassung, wenn das letzte Element in der Versionsgeschichte mit der Tastenkombination NACH-OBEN+EINGABE erneut ausgeführt wird, wobei die Bearbeitung eines mehrzeiligen Codeblocks durch Drücken der NACH-OBEN-TASTE natürlich zugelassen wird, damit Sie darin navigieren können.

Um die Navigation in mehrzeiligen Codeblöcken zu vermeiden, verwenden Sie die Schaltflächen der Symbolleiste oder ALT+NACH-OBEN und ALT+NACH-UNTEN, damit alle Blöcke als einzelne Zeile behandelt werden.

Der einfachste Weg zum Kennenlernen der Verlaufsfeatures ist, diese selbst im interaktiven Fenster zu testen. Der unten dargestellte Code stellt einige passende einzeilige und mehrzeilige Anweisungen dar. Kopieren Sie jede Anweisung und fügen Sie sie einzeln ein, um die passende Versionsgeschichte zu erstellen. (Sie können den Code auch in eine separate Codedatei einfügen und die Zeilen mithilfe von STRG+EINGABE an das interaktive Fenster senden.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```
