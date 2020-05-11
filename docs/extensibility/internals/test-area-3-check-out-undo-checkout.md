---
title: 'Testbereich 3: Checkout &0Er-Auschecken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704615"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testbereich 3: Auschecken/Auschecken rückgängig machen
Dieser Quellcodeverwaltungs-Plug-In-Testbereich behandelt das Bearbeiten und Zurücksetzen von Elementen aus dem Versionsspeicher über die Befehle **Auschecken** und **Auschecken rückgängig machen.**

**Auschecken**: Markiert ein Element im Versionsspeicher als ausgecheckt, ändert die lokale Kopie zum Lesen/Schreiben.

**Auschecken rückgängig machen:** Markiert ein Element im Versionsspeicher als eingecheckt, stellt die lokale Kopie in den Status vor dem Auschecken zurück (abhängig von den Optionen).

## <a name="command-menu-access"></a>Befehlsmenüzugriff

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für Entwicklungsumgebungen verwendet.

##### <a name="check-out"></a>Auschecken:

- **Datei**, **Quellcodeverwaltung**, **Auschecken**.

- **Datei**, **Auschecken**.

- Shortcut-Menü, **Auschecken**.

- Auschecken rückgängig machen: **Datei**, **Quellcodeverwaltung**, **Auschecken rückgängig**machen .

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten

- Nach dem Auscheckvorgang werden die Zieldatei(en) und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher schreibt dem richtigen Benutzer das Auschecken zu.

- Die Uhrzeit und das Datum des Auscheckens sind korrekt (gemäß den Einstellungen des Benutzers).

## <a name="test-cases"></a>Testfälle

Im Folgenden finden Sie spezifische Testfälle für den Testbereich Checkout/Undo Checkout.

### <a name="case-3a-check-out"></a>Fall 3a: Check Out

Dieser Abschnitt konzentriert sich auf die Bedienung des Auscheckbefehls.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Auschecken Exklusiv (COE) ein Client-Projekt|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schauen Sie sich das gesamte Projekt exklusiv (**Datei**, **Auschecken**).|Check-out erfolgt.|
|Auschecken exklusiv (COE) ein Dateisystem oder lokales IIS-Webprojekt|1. Legen Sie die Webserververbindung auf Dateifreigabe in **Tools**, **Optionen**, **Projekte**, **Webeinstellungen**.<br />2. Erstellen Sie ein Webprojekt.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Schauen Sie sich das gesamte Projekt exklusiv (**Datei**, **Quellcodeverwaltung**, **Auschecken**).|Check-out erfolgt.|
|Auschecken von Lösungselementen in einer Lösung (neue Methode zur Behandlung anderer Dateien)|1. Erstellen Sie eine leere Lösung.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schauen Sie sich die Lösung an.<br />4. Fügen Sie mehrere Lösungselemente hinzu.<br />5. Checken Sie alle neu hinzugefügten Elemente ein.<br />6. Wählen Sie mehrere Lösungselemente aus.<br />7. Schauen Sie sich die ausgewählten Elemente (Shortcut-Menü, **Auschecken**) an.|Ausgewählte Dateien werden ausgecheckt.|
|Auschecken der lokalen Version (wenn das im Test befindliche Plug-In diese Funktion unterstützt)|1. Benutzer 1: Erstellen Sie ein Clientprojekt.<br />2. Benutzer 1: Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Benutzer 2: Öffnen Sie die Lösung von der Quellcodeverwaltung zu einem anderen Ort.<br />4. Benutzer 2: Schauen Sie sich eine Datei an.<br />5. Benutzer 2: Ändern Sie die Datei.<br />6. Benutzer 2: Checken Sie die Datei ein.<br />7. Benutzer 1: Auschecken der lokalen Version der Datei (Überprüfen Sie die erweiterte Option **Auschecken der lokalen Version** im Dialogfeld **Auschecken).**|Die lokale Version der Datei ist ausgecheckt.<br /><br /> Änderungen von Benutzer 2 werden nicht auf die Datei "Benutzer 1" angewendet.|

### <a name="case-3b-disconnected-check-out"></a>Fall 3b: Getrenntes Auschecken

Der Betrieb im getrennten Modus ermöglicht Benutzern eine gewisse Unterstützung der fortgesetzten Quellcodeverwaltung, wenn sie nicht direkt an einen Versionsspeicher angeschlossen sind. Dies geschieht, indem alle relevanten Informationen über die eingetragene Projektmappe und Projekte lokal zwischengesetzt werden.

Exklusive Auscheckvorgänge können nur ausgeführt werden, wenn sie mit dem Quellcodeverwaltungsspeicher verbunden sind. Freigegebene Auscheckvorgänge können jederzeit erfolgen, unabhängig davon, ob sie verbunden oder getrennt sind. Wenn die Verbindung zum Versionsspeicher getrennt wird, ist daher nur der Befehl **"Freigegeben auschecken"** (COS) aktiviert. Während der Verbindung wird **das Auschecken** rückgängig gemacht deaktiviert, da die alte Version nicht abgerufen werden kann, um die vom Benutzer vorgenommenen Änderungen zu ersetzen.

Wenn der Benutzer erneut eine Verbindung mit dem Versionsspeicher herstellt, werden die Auscheckstatus aller eingetragenen Projektlösungen und Projekte synchronisiert. Dadurch werden die erforderlichen Aktualisierungen des Speichers für die vom Benutzer ausgeführten Auscheckungen durchgeführt. Sobald die Synchronisierung erfolgt ist, kann der Benutzer normal weiterarbeiten (verbunden).

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Der Befehl **Auschecken** kann nicht exklusiv verwendet werden, während die Verbindung zum Versionsspeicher getrennt ist.

- Der Befehl **Auschecken** rückgängig machen kann nicht verwendet werden, während die Verbindung zum Versionsspeicher getrennt ist.

- Der Befehl **"Shared Check Out"** funktioniert.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Während der Verbindung eine Datei auschecken und dann eine Verbindung zum Synchronisieren herstellen|1. Trennen Sie ein gesteuertes Projekt mithilfe des Dialogfelds Quellcodeverwaltung ändern (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />2. Überprüfen Sie eine Datei aus.<br />3. Klicken Sie im Warndialogfeld auf Auschecken (getrennt).<br />4. Bearbeiten Sie die Datei.<br />5. Verbinden Sie sich über das Dialogfeld Quellcodeverwaltung ändern.<br />6. Holen Sie sich die neueste Version der bearbeiteten Datei.|Häufiges erwartetes Verhalten|

### <a name="case-3c-query-editquery-save-qeqs"></a>Fall 3c: Abfragebearbeitung/Abfragespeicherung (QEQS)
 Elemente unter Quellcodeverwaltung werden für Änderungen, Änderungen und Speicher nachverfolgt, um Benutzern die einfache Verwaltung ihrer Dateien zu erleichtern. Wenn ein gesteuertes Element, das "eingecheckt" ist, bearbeitet wird, fängt QEQS die versuchte Bearbeitung ab und fragt den Benutzer, ob er die Datei auschecken möchte, um sie zu bearbeiten. Abhängig von den Einstellungen **für Tools**, **Optionen** ist der Benutzer entweder gezwungen, die Datei auszuchecken, um sie zu bearbeiten, oder kann eine Kopie im Arbeitsspeicher bearbeiten und später auschecken. Wenn die Einstellung **Extras**, **Optionen** des Benutzers nicht so eingestellt ist, dass das Auscheck-Dialogfeld angezeigt wird und es einfach ausgecheckt wird, wird die Datei automatisch ausgecheckt, wenn dies möglich ist.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Nach dem Auscheckvorgang werden die Zieldatei(en) und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher schreibt das Auschecken dem richtigen Benutzer zu.

- Die Uhrzeit und das Datum des Auscheckens sind korrekt (gemäß den Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Zielordners ist schreibbar.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Bearbeiten einer eingecheckten Textdatei|1. Erstellen Sie ein neues Projekt, das eine Textdatei enthält.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Set **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeiten lassen, während schreibgeschützt auf dem Datenträger** deaktiviert werden.<br />4. Set **Tools**, **Optionen**, **Quellcodeverwaltung**, **Eingabeaufforderung für das Auschecken** in **der, wenn eingecheckte Dateien werden Combo-Feld bearbeitet.**<br />5. Set **Tools**, **Optionen**, **Quellcodeverwaltung**, **Aufforderung zum Auschecken** in **der, wenn eingecheckte Dateien gespeichert werden** Combo-Feld.<br />6. Öffnen Sie textdatei im Editor, versuchen Sie, neuen Text in die Datei einzugeben. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Dialogfeld **Auschecken für Bearbeiten** auf **Abbrechen.** Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />8. Set **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeiten lassen, während schreibgeschützt auf dem Datenträger** überprüft werden.<br />9. Öffnen Sie die Projektdatei im Editor, versuchen Sie, neuen Text in die Datei einzugeben. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />10. Klicken Sie im Dialogfeld **Auschecken für Bearbeiten** auf **Bearbeiten.** Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />11. Bearbeiten Sie die Textdatei und versuchen Sie, sie zu speichern.|`Result of step 6:`<br /><br /> Das Dialogfeld Bearbeiten wird angezeigt.<br /><br /> `Result of step 7:`<br /><br /> Die Datei ist unverändert.<br /><br /> `Result of step 9:`<br /><br /> Das Dialogfeld Bearbeiten wird angezeigt.<br /><br /> `Result of step 10:`<br /><br /> Sie können die Projektdatei im Arbeitsspeicher bearbeiten.<br /><br /> `Result of step 11:`<br /><br /> Beim Speichern wird das Dialogfeld Beim Speichern angezeigt.|
|Bearbeiten einer eingecheckten Projektmappendatei|Wiederholen Sie die Schritte, wie im vorherigen Test beschrieben, aber ändern Sie die Projektmappe, anstatt eine Textdatei zu ändern, indem Sie die Lösungseigenschaften ändern.|Wie bei vorherigem Test|
|Bearbeiten einer Projektdatei, die eingecheckt ist|Wiederholen Sie die Schritte, wie im vorherigen Test beschrieben, aber ändern Sie das Projekt, anstatt eine Textdatei zu ändern, indem Sie die Projekteigenschaften ändern.|Genauso wie der vorherige Test.|

### <a name="case-3d-silent-check-out"></a>Fall 3d: Silent Check Out
 Dieser Unterbereich behandelt Auscheckszenarien, in denen **das** Dialogfeld Auschecken nicht pro Benutzer extra **,** **Optionen**, **Quellcodeverwaltungseinstellungen**angezeigt wird.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Nach dem Auscheckvorgang werden die Zieldatei(en) und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher schreibt das Auschecken dem richtigen Benutzer zu.

- Die Uhrzeit und das Datum des Auscheckens sind korrekt (gemäß den Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Zielordners ist schreibbar.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Stilles Auschecken für eine Datei|1. Set **Tools**, **Optionen**, **Source Control,** um **Dateien automatisch bei bearbeiten auszuchecken**.<br />2. Erstellen Sie ein neues Projekt mit einer Datei.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Schauen Sie sich die Datei an.|Die Datei wird im Hintergrund ausgecheckt (keine Benutzeroberfläche).|
|Stille Kasse für ein Projekt|1. Set **Tools**, **Optionen**, **Source Control,** um **Dateien automatisch bei bearbeiten auszuchecken**.<br />2. Erstellen Sie ein neues Projekt.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Schauen Sie sich das Projekt an.|Die Datei wird im Hintergrund ausgecheckt (keine Benutzeroberfläche).|

### <a name="case-3e-undo-check-out"></a>Fall 3e: Auschecken rückgängig machen
 **Auschecken** rückgängig machen wird verwendet, um den ausgecheckten Status einer Datei abzubrechen und das Einchecken von Änderungen an der Datei zu vermeiden.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Die Standardeinstellung basiert auf der Einstellung **Lokalversion auschecken.** Wenn der Benutzer die lokale Version auschecken möchte, ist die Standardeinstellung für das Rückgängigmachen immer die ausgecheckte Version.

- Nach Annahme des Rückgängigmachens werden die Symbole im **Projektmappen-Explorer** für betroffene Dateien aktualisiert, und das Element wird aus dem Fenster **Ausstehende Eincheckungen** entfernt.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Auschecken einer einzelnen Datei rückgängig machen, die exklusiv ausgecheckt ist|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schauen Sie sich eine Datei exklusiv an.<br />4. Ändern Sie die Datei.<br />5. Auschecken rückgängig machen (**Datei**, **Quellcodeverwaltung**, **Auschecken rückgängig machen**).|Häufiges erwartetes Verhalten.|
|Auschecken einer einzelnen Datei rückgängig machen, die ausgecheckt ist Freigegeben|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schauen Sie sich eine freigegebene Datei an.<br />4. Ändern Sie die Datei.<br />5. Auschecken rückgängig machen (**Datei**, **Quellcodeverwaltung**, **Auschecken rückgängig machen**).|Häufiges erwartetes Verhalten.|
|Auschecken eines Projekts nach dem Hinzufügen von Dateien zum Projekt rückgängig machen|1. Erstellen Sie ein neues Projekt und fügen Sie es der Quellcodeverwaltung hinzu.<br />2. Schauen Sie sich das Projekt an.<br />3. Fügen Sie dem Projekt eine Datei hinzu.<br />4. Auschecken des Projekts rückgängig machen.|Die hinzugefügte Datei wird aus dem Projekt projektmappen-Explorer entfernt.<br /><br /> Das Projekt ist nicht mehr ausgecheckt.|
|Auschecken eines Projekts nach dem Löschen von Dateien aus dem Projekt rückgängig machen|1. Erstellen Sie ein neues Projekt und fügen Sie es der Quellcodeverwaltung hinzu.<br />2. Schauen Sie sich das Projekt an.<br />3. Löschen Sie eine Datei aus dem Projekt.<br />4. Auschecken des Projekts rückgängig machen.|Gelöschte Datei wird im Projektmappen-Explorer unter dem Projektmappen-Explorer angezeigt.<br /><br /> Das Projekt ist nicht mehr ausgecheckt.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
