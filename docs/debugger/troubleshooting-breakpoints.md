---
title: Problembehandlung von Haltepunkten in Visual Studio-Debugger | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d587809a9690e312e923ba184c9d90c38405a5d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Problembehandlung von Haltepunkten in Visual Studio-Debugger

## <a name="breakpoint-warnings"></a>Haltepunkt-Warnungen

Ein Haltepunkt verfügt über zwei mögliche visuelle Zustände beim Debuggen: ausgefüllter roten Kreis und ein leerer (weiß gefüllt) Kreis. Wenn der Debugger einen Haltepunkt im Zielprozess erfolgreich festlegen kann, bleibt die roten ausgefüllter Kreis. Ist zum Haltepunkt einen Kreis, der Haltepunkt ist deaktiviert oder Warnung aufgetreten beim Versuch, die der Breakpoint festgelegt ist. Um den Unterschied zu bestimmen, zeigen Sie auf den Haltepunkt aus, und ermitteln Sie, ob eine Warnung.

Die folgenden beiden Abschnitten wird beschrieben, deutliche Warnungen und wie sie diesen Fehler beheben. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Keine Symbole haben für dieses Dokument geladen wurde." 

Wechseln Sie zu der **Module** Fenster (**Debuggen** > **Windows** > **Module**) und überprüft, ob das Modul geladen.  
* Wenn Ihr Modul geladen wird, überprüfen Sie die **Symbolstatus** Spalte, um festzustellen, ob Symbole geladen wurden. 
  * Wenn keine Symbole geladen sind, überprüfen Sie den Symbolstatus, um das Problem zu diagnostizieren. Klicken Sie im Kontextmenü für ein Modul in der **Module** Fenster, klicken Sie auf **Symbolladeinformationen...**  angezeigt, in dem der Debugger gesucht, versuchen Sie es, und Laden von Symbolen. Weitere Informationen zum Laden von Symbolen finden Sie unter [angeben von Symboldateien (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Wenn Sie Symbole geladen sind, bedeutet dies, dass die PDB-Datei keine Informationen zu den Quelldateien enthält. Dies sind einige mögliche Ursachen: 
    * Wenn Ihre Quelldateien vor kurzem hinzugefügt wurden, vergewissern Sie sich, dass eine aktuelle Version des Moduls geladen wird.  
    * Es ist möglich, erstellen reduzierte PDB-Dateien, die mit der **/PDBSTRIPPED** (Linkeroption). Reduzierte PDB-Dateien enthalten keine Informationen zur Quelldatei. Vergewissern Sie sich, dass Sie eine vollständige PDB-Datei und keine reduzierte PDB-Datei verwenden.  
    * Die PDB-Datei ist teilweise fehlerhaft. Versuchen Sie die Datei zu löschen und einen bereinigten Build des Moduls an, wenn diese finden Sie unter ausführen, wird das Problem behoben. 

* Wenn das Modul nicht geladen wurde, überprüfen Sie Folgendes ein, um die Ursache zu ermitteln: 
  * Vergewissern Sie sich, dass Sie den richtigen Prozess debuggen. 
  * Stellen Sie sicher, dass Sie die richtige Art von Code Debuggen. Sie können feststellen, welche Art von Code, die der Debugger so konfiguriert ist, dass das Debuggen in der **Prozesse** Fenster (**Debuggen** > **Windows**  >  **Prozesse**). Z. B. Wenn Sie C#-Code debuggen möchten, vergewissern Sie sich, dass der Debugger für den entsprechenden .NET Framework-Typ konfiguriert ist (z. B. verwaltet (v4\*) im Vergleich zu Managed (v2\*/v3\*) im Vergleich zu Managed (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… der aktuellen Quellcode unterscheidet sich von der Version integriert..." 

Wenn eine Quelldatei geändert wurde, und die Quelle nicht mehr mit dem Code übereinstimmt, den Sie Debuggen, wird der Debugger keine Haltepunkte im Code standardmäßig festgelegt. Fall in der Regel wird dieses Problem auf, wenn eine Quelldatei geändert wird, aber der Quellcode wurde nicht neu erstellt. Um dieses Problem zu beheben, müssen Sie das Projekt neu. Wenn das Buildsystem geht davon aus, dass das Projekt bereits auf dem neuesten Stand ist, obwohl dies nicht der Fall, können Sie das Projektsystem, neu erstellen, entweder indem Sie die Quelldatei erneut speichern, oder Bereinigen des Projekts zu erstellen, indem die Ausgabe vor dem Erstellen erzwingen. 

In seltenen Szenarien können Sie ohne entsprechende Quellcode debuggen möchten. Dies kann dazu führen, dass eine Debugleistung erzielen Sie sehr verwirrend, achten Sie darauf, dass dies wie soll der Vorgang fortgesetzt wird.  

Führen Sie eine der folgenden Aktionen aus, um diese sicherheitsüberprüfungen deaktivieren: 
* Um einen einzelnen Breakpoint zu ändern, zeigen Sie auf das Symbol "Haltepunkt" im Editor aus, und klicken Sie auf das Symbol "Einstellungen" (Zahnrad) ". Der Editor wird einem Peek-Fenster hinzugefügt. Am oberen Rand des Peek-Fensters ist ein Hyperlink, der die Position des Haltepunkts angibt. Klicken Sie auf den Link, um die Änderung von der Position des Haltepunkts zu ermöglichen, und überprüfen Sie **Quellcode vom Original unterscheiden zulassen**.
* Um diese Einstellung für alle Haltepunkte zu ändern, wechseln Sie zu **Debuggen** > **Optionen und Einstellungen**. Deaktivieren Sie auf der Seite **Debugging/Allgemein** das Kontrollkästchen **Quelldateien müssen exakt mit der Originalversion übereinstimmen** . Stellen Sie sicher, dass diese Option erneut zu aktivieren, wenn Sie fertig sind Debuggen. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Der Breakpoint (keine Warnung) wurde erfolgreich festgelegt, aber nicht erreicht 

Dieser Abschnitt enthält Informationen zum Behandeln von Problemen, wenn der Debugger wird keine Warnungen anzeigen – der Haltepunkt eine durchgehende roter Kreis ist während des Debuggens aktiv, aber wird nicht der Haltepunkt erreicht wird. 

Hier sind einige Punkte zu überprüfen: 
1. Wenn der Code in mehr als einem Prozess oder mehr als einem Computer ausgeführt wird, stellen Sie sicher, dass Sie den richtigen Prozess oder Computer Debuggen.  
2. Vergewissern Sie sich, dass Ihr Code ausgeführt wird. Eine einfache Möglichkeit zum Testen besteht im Hinzufügen von eines Aufrufs von `System.Diagnostics.Debugger.Break` (C#/VB) oder `__debugbreak` (C++) auf die Codezeile, die Sie den Haltepunkt festlegen, und erstellen Sie das Projekt dann erneut versuchen. 
3. Wenn Sie optimierten Code Debuggen, stellen Sie sicher, dass die Funktion, in denen der Haltepunkt festgelegt ist, wird nicht wird in eine andere Funktion inline erweitert. Die `Debugger.Break` bei der vorherigen Prüfung beschriebenen Test kann zusammenarbeiten, um dies ebenfalls zu testen. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Ich habe einen Haltepunkt gelöscht, aber erreiche ihn beim erneuten Debuggen weiterhin 

Wenn Sie einen Haltepunkt während des Debuggens gelöscht haben, können Sie den nächsten Haltepunkt Debuggen. Zum Beenden des Erreichens dieses Haltepunkt müssen Sie sicherstellen, dass alle Instanzen des Haltepunkts aus dem Fenster **Haltepunkte** entfernt wurden.  
