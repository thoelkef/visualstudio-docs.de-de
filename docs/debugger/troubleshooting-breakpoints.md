---
title: Behandeln von Problemen mit Breakpoints im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c11741cb9bb9a0b0c64b9452b54daa6ac226b92
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535927"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Behandeln von Problemen mit Breakpoints im Visual Studio-Debugger

## <a name="breakpoint-warnings"></a>Haltepunkt Warnungen

Beim Debuggen verfügt ein Haltepunkt über zwei mögliche visuelle Zustände: einen ausgefüllten roten Kreis und einen hohlen (weißen gefüllten) Kreis. Wenn der Debugger erfolgreich einen Haltepunkt im Ziel Prozess festlegen kann, bleibt er ein roter roter Kreis. Wenn der Haltepunkt ein leerer Kreis ist, ist entweder der Breakpoint deaktiviert, oder es ist eine Warnung beim Versuch aufgetreten, den Haltepunkt festzulegen. Um den Unterschied zu ermitteln, zeigen Sie auf den Haltepunkt, und prüfen Sie, ob eine Warnung vorliegt.

In den folgenden beiden Abschnitten werden wichtige Warnungen und deren Behebung beschrieben.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>„No Symbols have been loaded for this document“ (Für dieses Dokument wurden keine Symbole geladen)

Wechseln Sie zum Fenster " **Module** " (**Debuggen**  > **Windows**  > **Module**), und überprüfen Sie, ob das Modul geladen ist.
* Wenn das Modul geladen ist, überprüfen Sie die Spalte **Symbol Status** , um festzustellen, ob Symbole geladen wurden.
  * Wenn keine Symbole geladen werden, überprüfen Sie den Symbol Status, um das Problem zu diagnostizieren. Klicken Sie im Kontextmenü eines Moduls im Fenster **Module** auf **Symbol ladeinformationen...** , um zu überprüfen, wo der Debugger versucht hat, Symbole zu laden und zu laden. Weitere Informationen zum Laden von Symbolen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Wenn Symbole geladen werden, enthält die PDB keine Informationen zu ihren Quelldateien. Dies sind einige mögliche Ursachen:
    * Wenn die Quelldateien kürzlich hinzugefügt wurden, vergewissern Sie sich, dass eine aktuelle Version des Moduls geladen wird.
    * Es ist möglich, gestreifte pdsb mithilfe der **/PDBSTRIPPED** (Linkeroption) zu erstellen. Entfernt-pdsb enthalten keine Quelldatei Informationen. Vergewissern Sie sich, dass Sie mit einer vollständigen PDB-Datei arbeiten und nicht mit einer abgestürzten PDB
    * Die PDB-Datei ist teilweise beschädigt. Löschen Sie die Datei, und führen Sie einen bereinigen Build des Moduls aus, um das Problem zu beheben.

* Wenn das Modul nicht geladen ist, überprüfen Sie Folgendes, um die Ursache zu ermitteln:
  * Vergewissern Sie sich, dass Sie den richtigen Prozess Debuggen.
  * Stellen Sie fest, dass Sie die richtige Art von Code Debuggen. Sie können herausfinden, welche Art von Code der Debugger für das Debuggen im Fenster " **Prozesse** " (**Debuggen**  > **Windows**  > **Prozesse**) konfiguriert ist. Wenn Sie z. b. versuchen, Code C# zu debuggen, vergewissern Sie sich, dass der Debugger für den entsprechenden Typ und die entsprechende Version von .NET konfiguriert ist (z. b. Managed (v4 \*) oder Managed (v2 \*/V3 \*) und Managed (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… der aktuelle Quellcode unterscheidet sich von der in integrierte Version... "

Wenn eine Quelldatei geändert wurde und die Quelle nicht mehr mit dem Code übereinstimmt, den Sie Debuggen, legt der Debugger standardmäßig keine Breakpoints im Code fest. Normalerweise tritt dieses Problem auf, wenn eine Quelldatei geändert wird, der Quellcode jedoch nicht neu erstellt wurde. Um dieses Problem zu beheben, erstellen Sie das Projekt neu. Wenn das Buildsystem davon ausgeht, dass das Projekt bereits auf dem neuesten Stand ist, auch wenn dies nicht der Fall ist, können Sie das erneute Erstellen des Projekt Systems erzwingen, indem Sie die Quelldatei erneut speichern oder die Buildausgabe des Projekts vor dem Erstellen bereinigen.

In seltenen Szenarien können Sie Debuggen, ohne dass der Quellcode übereinstimmt. Das Debuggen ohne übereinstimmenden Quellcode kann zu einer verwirrenden debuggingdarstellung führen. Stellen Sie daher sicher, dass Sie den Vorgang fortsetzen möchten.

Um diese Sicherheitsüberprüfungen zu deaktivieren, führen Sie einen der folgenden Schritte aus:
* Um einen einzelnen Haltepunkt zu ändern, bewegen Sie den Mauszeiger über das Haltepunkt Symbol im Editor, und klicken Sie auf das Symbol "Einstellungen" (Zahnrad). Dem Editor wird ein Peek-Fenster hinzugefügt. Am oberen Rand des Peek-Fensters gibt es einen Hyperlink, der den Speicherort des Breakpoints angibt. Klicken Sie auf den Hyperlink, um Änderungen an der Haltepunkt Position zuzulassen, und aktivieren Sie **die Option zulassen, dass der Quellcode vom ursprünglichen**abweicht.
* Um diese Einstellung für alle Breakpoints zu ändern, wechseln Sie zu **Debug > ** **Optionen und Einstellungen**. Deaktivieren Sie auf der Seite **Debugging/Allgemein** das Kontrollkästchen **Quelldateien müssen exakt mit der Originalversion übereinstimmen** . Stellen Sie sicher, dass Sie diese Option erneut aktivieren, wenn Sie das Debugging abgeschlossen haben.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Der Breakpoint wurde erfolgreich festgelegt (keine Warnung), aber nicht gefunden.

Dieser Abschnitt enthält Informationen zur Problembehandlung, wenn der Debugger keine Warnungen anzeigt – bei dem Haltepunkt handelt es sich um einen voll Hand roten Kreis, während das aktive Debuggen ausgeführt wird, aber der Breakpoint wird nicht gedrückt.

Folgende Punkte müssen überprüft werden:
1. Wenn Ihr Code in mehr als einem oder mehreren Computern ausgeführt wird, müssen Sie sicherstellen, dass Sie den richtigen Prozess oder Computer Debuggen.
2. Vergewissern Sie sich, dass der Code ausgeführt wird. Um zu testen, ob der Code ausgeführt wird, fügen Sie der Codezeile, in der der Breakpoint festgelegt werden soll, einen `System.Diagnostics.Debugger.Break` (C#/VB) oder `__debugbreak` (C++)-Befehl hinzu, und erstellen Sie dann das Projekt neu.
3. Wenn Sie optimierten Code Debuggen, stellen Sie sicher, dass die Funktion, in der der Breakpoint festgelegt ist, nicht in einer anderen Funktion Inline ist. Der in der vorherigen Überprüfung beschriebene `Debugger.Break` Test kann auch zum Testen dieses Problems funktionieren.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Ich habe einen Haltepunkt gelöscht, aber erreiche ihn beim erneuten Debuggen weiterhin

Wenn Sie während des Debuggens einen Haltepunkt gelöscht haben, können Sie beim nächsten Start des Debuggens erneut den Haltepunkt erreichen. Zum Beenden des Erreichens dieses Haltepunkt müssen Sie sicherstellen, dass alle Instanzen des Haltepunkts aus dem Fenster **Haltepunkte** entfernt wurden.
