---
title: Problembehandlung von Haltepunkten im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbcda5eef8ac6ac6aa20c6f487dfc94beb10866c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929664"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Problembehandlung von Haltepunkten in Visual Studio-Debugger

## <a name="breakpoint-warnings"></a>Haltepunkt-Warnungen

Ein Haltepunkt verfügt über zwei mögliche visuelle Zustände beim Debuggen: einen ausgefüllten roten Kreis und ein leerer (weiß gefüllt) Kreis. Wenn der Debugger erfolgreich einen Haltepunkt im Zielprozess festlegen kann, bleibt sie einen ausgefüllten roten Kreis. Wenn der Breakpoint ein leerer Kreis ist, der Haltepunkt ist deaktiviert oder Warnung trat beim Versuch, die der Haltepunkt gesetzt. Um den Unterschied zu bestimmen, zeigen Sie auf den Haltepunkt, und prüfen Sie, ob eine Warnung aus.

Die folgenden beiden Abschnitte beschreiben die deutliche Warnungen und zur Behebung dieser Probleme.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>„No Symbols have been loaded for this document“ (Für dieses Dokument wurden keine Symbole geladen)

Wechseln Sie zu der **Module** Fenster (**Debuggen** > **Windows** > **Module**) und überprüft, ob Ihr Modul geladen.
* Wenn Ihr Modul geladen wird, überprüfen Sie die **Symbolstatus** Spalte, um festzustellen, ob Symbole geladen wurden.
  * Wenn keine Symbole geladen sind, überprüfen Sie den Symbolstatus, um das Problem zu diagnostizieren. Klicken Sie im Kontextmenü für ein Modul in die **Module** Fenster, klicken Sie auf **Symbolladeinformationen...**  angezeigt, in denen der Debugger gesucht, versuchen Sie es aus, und Laden von Symbolen. Weitere Informationen zum Laden von Symbolen finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Wenn Symbole geladen sind, enthält die PDB-Datei keine Informationen zu den Quelldateien. Dies sind einige mögliche Ursachen:
    * Wenn Ihre Quelldateien vor kurzem hinzugefügt wurden, vergewissern Sie sich, dass eine aktuelle Version des Moduls geladen wird.
    * Es ist möglich, erstellen Sie entfernte PDBs, die mit der **/PDBSTRIPPED** -Linkeroption. Entfernte PDBs enthalten keine Informationen zur Quelldatei. Vergewissern Sie sich, dass Sie mit einem vollständigen PDB-Datei und keine bereinigte PDB-Datei bearbeitet werden.
    * Die PDB-Datei ist teilweise fehlerhaft. Löschen Sie die Datei, und führen Sie einen bereinigten Build des Moduls, um das Problem zu beheben.

* Wenn Ihr Modul nicht geladen ist, überprüfen Sie Folgendes ein, um die Ursache zu ermitteln:
  * Vergewissern Sie sich, dass Sie den richtigen Prozess debuggen.
  * Überprüfen, ob Sie die richtige Art von Code Debuggen. Sie können herausfinden, welche Art von Code, die der Debugger so konfiguriert ist, dass das Debuggen in der **Prozesse** Fenster (**Debuggen** > **Windows**  >  **Prozesse**). Z. B. Wenn Sie versuchen, C#-Code zu debuggen, vergewissern Sie sich, dass der Debugger für den entsprechenden .NET Framework konfiguriert ist (z. B. verwaltet (v4\*) im Vergleich zu verwalteter (v2\*/v3\*) im Vergleich zu verwalteter (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… der aktuelle Quellcode unterscheidet sich von der Version, erstellt in..."

Wenn eine Quelldatei geändert wurde, und die Quelle nicht mehr mit dem Code übereinstimmt, den Sie Debuggen, wird der Debugger keine Haltepunkte im Code standardmäßig festgelegt. Dieses Problem in der Regel geschieht, wenn eine Quelldatei geändert wird, aber der Quellcode wurde nicht neu erstellt. Um dieses Problem zu beheben, müssen Sie das Projekt neu. Wenn das Buildsystem geht davon aus, dass das Projekt bereits auf dem neuesten Stand ist, obwohl dies nicht der Fall ist, können Sie das Projektsystem neu erstellen, entweder indem Sie die Quelldatei erneut speichern, oder Bereinigen des Projekts erstellen vor dem Erstellen von erzwingen.

In seltenen Szenarien empfiehlt es sich um ohne entsprechenden Quellcode zu debuggen. Ohne entsprechendes Quellcode debuggen kann zu einer verwirrenden Debuggingumgebung, also sicherstellen, dass sieht, wie Sie fortfahren möchten.

Führen Sie eine der folgenden Schritte aus, um diese sicherheitsüberprüfungen zu deaktivieren:
* Um einen einzelnen Breakpoint zu ändern, zeigen Sie auf das Symbol "Haltepunkt" im Editor, und klicken Sie auf das einstellungssymbol (Zahnrad). Der Editor wird einem Peek-Fenster hinzugefügt. Am oberen Rand der Peek-Fenster gibt es ein Link, der den Speicherort des Haltepunkts angibt. Klicken Sie auf den Link, um die Änderung der Haltepunktposition zulassen, und überprüfen Sie **können Sie den Quellcode vom Original unterscheiden**.
* Um diese Einstellung für alle Haltepunkte zu ändern, wechseln Sie zu **Debuggen** > **Optionen und Einstellungen**. Deaktivieren Sie auf der Seite **Debugging/Allgemein** das Kontrollkästchen **Quelldateien müssen exakt mit der Originalversion übereinstimmen** . Stellen Sie sicher, dass diese Option wieder zu aktivieren, wenn Sie fertig sind Debuggen.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Der Haltepunkt wurde erfolgreich (keine Warnung) festgelegt, aber nicht erreicht

Dieser Abschnitt enthält Informationen zum Behandeln von Problemen, wenn der Debugger wird keine Warnungen angezeigt: der Haltepunkt einen ausgefüllten roten Kreis, wird während Sie aktiv Debuggen, aber ist nicht der Haltepunkt erreicht wird.

Hier sind einige Punkte zu überprüfen:
1. Wenn Ihr Code in mehr als einem Prozess oder mehr als einem Computer ausgeführt wird, stellen Sie sicher, dass Sie den richtigen Prozess oder Computer Debuggen.
2. Vergewissern Sie sich, dass Ihr Code ausgeführt wird. Um zu testen, dass Ihr Code ausgeführt wird, fügen Sie einen Aufruf von `System.Diagnostics.Debugger.Break` (C#/VB) oder `__debugbreak` (C++) zu der Codezeile, in dem Sie versuchen, legen Sie den Haltepunkt, und erstellen Sie das Projekt dann erneut.
3. Wenn Sie optimierten Code Debuggen, stellen Sie sicher, dass die Funktion, in der der Haltepunkt festgelegt, ist nicht wird inline in eine andere Funktion. Die `Debugger.Break` Tests beschrieben, die in der vorherigen Überprüfung kann zusammenarbeiten, um dieses Problem und zu testen.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Ich habe einen Haltepunkt gelöscht, aber erreiche ihn beim erneuten Debuggen weiterhin

Wenn Sie einen Haltepunkt während des Debuggens gelöscht haben, können Sie den nächsten Haltepunkt Debuggen. Zum Beenden des Erreichens dieses Haltepunkt müssen Sie sicherstellen, dass alle Instanzen des Haltepunkts aus dem Fenster **Haltepunkte** entfernt wurden.
