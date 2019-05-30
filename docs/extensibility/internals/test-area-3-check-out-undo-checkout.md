---
title: 'Testbereich 3: Check Out rückgängig: Auschecken | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93ca3f2c656c6bea81139e5e6101499a7fc8febd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331068"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testbereich 3: Auschecken / Auschecken rückgängig machen
Quellcodeverwaltung-Plug-in Test Hierunter bearbeiten und Zurücksetzen der Elemente aus dem Versionsspeicher über die **Auschecken** und **Rückgängig: Auschecken** Befehle.

**Sehen Sie sich**: Markiert ein Element in den Versionsspeicher als ausgecheckt, wird die lokale Kopie Lese-/Schreibzugriff geändert.

**Rückgängig: Auschecken**: Markiert ein Element in den Versionsspeicher als eingecheckt wird die lokale Kopie für den Zustand vor dem Auschecken (je nach Optionen) zurückgesetzt.

## <a name="command-menu-access"></a>Menüzugriff Befehl

Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen.

##### <a name="check-out"></a>Abreise:

- **Datei**, **Quellcodeverwaltung**, **Auschecken**.

- **Datei**, **Auschecken**.

- Klicken Sie im Kontextmenü **Auschecken**.

- Rückgängig: Auschecken: **Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**.

## <a name="common-expected-behavior"></a>Allgemeine erwartet

- Nach dem Auschecken werden die Ziel-Dateien bzw. Ordner markiert, als im Versionsspeicher ausgecheckt.

- Der Versionsspeicher Attribute das Auschecken, an den richtigen Benutzer.

- Uhrzeit und Datum des Auscheckens sind richtige (pro-Einstellungen des Benutzers).

## <a name="test-cases"></a>Testfälle

Im folgenden finden bestimmte Testfälle für den Testbereich "Auschecken rückgängig: Auschecken /".

### <a name="case-3a-check-out"></a>Groß-/Kleinschreibung 3a: Auschecken

Dieser Abschnitt konzentriert sich auf den Betrieb des Befehls Auschecken.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Überprüfen Sie, exklusive (festgestellte) eines Clientprojekts|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Sehen Sie sich das gesamte Projekt exklusiv (**Datei**, **Auschecken**).|Sehen Sie sich auftritt.|
|Sehen Sie sich exklusiven (festgestellte), einem Dateisystem oder dem lokalen IIS-Webprojekt|1.  Legen Sie die Web-Server-Verbindung mit der Dateifreigabe in **Tools**, **Optionen**, **Projekte**, **Webeinstellungen**.<br />2.  Erstellen Sie ein Webprojekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Sehen Sie sich das gesamte Projekt exklusiv (**Datei**, **Quellcodeverwaltung**, **Auschecken**).|Sehen Sie sich auftritt.|
|Sehen Sie sich Projektmappenelemente in einer Projektmappe (neue Methode für die Behandlung von anderen Dateien)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Überprüfen Sie die Lösung.<br />4.  Fügen Sie verschiedene Elemente der Lösung hinzu.<br />5.  Überprüfen Sie in alle neu hinzugefügten Elemente.<br />6.  Wählen Sie mehrere Elemente der Lösung.<br />7.  Sehen Sie sich die ausgewählten Elemente (klicken Sie im Kontextmenü **Auschecken**).|Ausgewählte Dateien werden ausgecheckt.|
|Lokale Version auschecken (sofern-Plug-in im Test dieses Feature unterstützt)|1.  Benutzer 1: Erstellen Sie ein Clientprojekt.<br />2.  Benutzer 1: Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Benutzer 2: Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einen anderen Speicherort.<br />4.  Benutzer 2: Sehen Sie sich eine Datei.<br />5.  Benutzer 2: Ändern Sie die Datei an.<br />6.  Benutzer 2: Überprüfen Sie in der Datei.<br />7.  Benutzer 1: Sehen Sie sich die lokale Version der Datei (Überprüfen Sie die **lokale Version Auschecken** erweiterte Optionen in **Auschecken** (Dialogfeld)).|Lokale Version der Datei wurde ausgecheckt.<br /><br /> Änderungen von Benutzer 2 gelten nicht für Benutzer 1 Datei.|

### <a name="case-3b-disconnected-check-out"></a>Fall 3 b: Nicht verbundene Auschecken

Im getrennten Modus kann Benutzer gewisse fortgesetzten quellcodeverwaltungsunterstützung Wenn nicht direkt an ein Versionsspeicher angefügt. Dies erfolgt, indem alle relevanten Informationen über die eingetragenen Projektmappen und Projekte lokal im Zwischenspeicher.

Exklusives Auschecken Vorgänge kann nur auftreten, während der Verbindung mit dem Speicher der quellcodeverwaltung. Freigegebenen Auschecken Vorgänge zu jedem Zeitpunkt ist möglich, ob verbunden oder getrennt. Aus diesem Grund, aus dem Versionsspeicher, nur die Verbindung getrennt die **überprüfen, freigegebene** (COS) Befehl aktiviert ist. Wenn Sie verbunden sind, **Rückgängig: Auschecken** ist deaktiviert, da die alte Version nicht abgerufen werden kann, um vom Benutzer vorgenommenen Änderungen zu ersetzen.

Wenn der Benutzer auf die Version die Verbindung wiederherstellt zu speichern, die Checkout-Status aller eingetragenen Lösungen und Projekte synchronisiert. Hierfür werden die erforderlichen Updates in den Speicher für das Auschecken, die der Benutzer ausgeführt hat. Nach die Synchronisierung stattgefunden hat, kann der Benutzer weiterhin wie gewohnt arbeiten (verbunden).

#### <a name="expected-behavior"></a>Es wird erwartet

- Können keine **ausschließlich Out** Befehl, wenn Sie aus dem Versionsspeicher verbunden.

- Können keine **Rückgängig: Auschecken** Befehl, wenn Sie aus dem Versionsspeicher verbunden.

- **Freigegebenen Auschecken** Befehl funktioniert.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Wenn Sie verbunden sind, sehen Sie sich eine Datei herstellen Sie, dann für die Synchronisierung|1.  Trennen Sie eine der quellcodeverwaltung unterliegenden Projekt mit Quellcodeverwaltung ändern (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />2.  Sehen Sie sich eine Datei.<br />3.  Klicken Sie auf diese Option, Auschecken (nicht verbunden), im Dialogfeld "Warnung".<br />4.  Bearbeiten Sie die Datei.<br />5.  Verbinden Sie das Dialogfeld "Quellcodeverwaltung ändern" verwenden.<br />6.  Erhalten Sie die neueste Version von die bearbeitete Datei.|Allgemeine erwartet|

### <a name="case-3c-query-editquery-save-qeqs"></a>Fall 3c: / Queryeditquerysave (QEQS.)
 Elemente in der quellcodeverwaltung werden für die Bearbeitung, Änderungen, nachverfolgt, und speichert, die Benutzer leichter verwalten ihrer Dateien. Wenn ein kontrollierter-Element, das "Einchecken" bearbeitet wird, wird QEQS fängt die versuchte Bearbeitung und fordert den Benutzer aus, wenn er die Datei so bearbeiten Sie es auschecken möchte. Je **Tools**, **Optionen** Einstellungen, die der Benutzer ist gezwungen, überprüfen Sie die Datei zum Bearbeiten auschecken mindestens berechtigt, auf die Kopie im Arbeitsspeicher bearbeiten, und sehen Sie sich später noch mal. Wenn des Benutzers **Tools**, **Optionen** Einstellung ist nicht festgelegt werden, um die sehen Sie sich das Dialogfeld anzuzeigen und gerade ausgecheckt, und klicken Sie dann wie der Benutzer seine bearbeiten trifft, die Datei automatisch ausgecheckt, wann immer möglich.

#### <a name="expected-behavior"></a>Es wird erwartet

- Nach dem Auschecken werden die Ziel-Dateien bzw. Ordner markiert, als im Versionsspeicher ausgecheckt.

- Der Versionsspeicher Attribute der sehen Sie sich an den richtigen Benutzer.

- Das Datum und Uhrzeit des das Auschecken sind richtige (pro-Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Ordners kann geschrieben werden.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Bearbeiten Sie die Textdatei, die eingecheckt wird|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** zu deaktiviert.<br />4.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Aufforderung zum Auschecken** in die **beim Einchecken werden Dateien bearbeitet** im Kombinationsfeld.<br />5.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Aufforderung zum Auschecken** in die **beim Einchecken werden Dateiengespeichert** im Kombinationsfeld.<br />6.  Öffnen Sie Text-Datei im Editor zu, die versuchen Sie, geben Sie den neuen Text in die Datei. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />7.  Klicken Sie auf **Abbrechen** in die **zum Bearbeiten auschecken** Dialogfeld. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />8.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** Option.<br />9. Öffnen Sie die Projektdatei im Editor, die versuchen Sie, geben Sie den neuen Text in der Datei. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />10. Klicken Sie auf **bearbeiten** in die **zum Bearbeiten auschecken** Dialogfeld. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />11. Bearbeiten Sie die Textdatei, und versuchen Sie, ihn zu speichern.|`Result of step 6:`<br /><br /> Sehen Sie sich für bearbeiten (Dialogfeld) wird angezeigt.<br /><br /> `Result of step 7:`<br /><br /> Die Datei bleibt unverändert.<br /><br /> `Result of step 9:`<br /><br /> Sehen Sie sich für bearbeiten (Dialogfeld) wird angezeigt.<br /><br /> `Result of step 10:`<br /><br /> Sie können die Projektdatei im Arbeitsspeicher bearbeiten.<br /><br /> `Result of step 11:`<br /><br /> Speichern wird auf die Prüfung, speichern Sie das Dialogfeld.|
|Bearbeiten Sie eine Projektmappendatei, die eingecheckt wird|Wiederholen Sie die Schritte wie beschrieben in vorherigen testen, aber anstatt zu ändern, eine Textdatei, die Projektmappe durch Ändern der Lösungseigenschaften von ändern.|Identisch mit den vorherigen test|
|Bearbeiten einer Projektdatei, die eingecheckt wird|Wiederholen Sie die Schritte wie beschrieben in vorherigen testen, aber anstelle eine Textdatei ändern, ändern Projekt durch Ändern von Projekteigenschaften.|Identisch mit den vorherigen Test.|

### <a name="case-3d-silent-check-out"></a>Case-3d: Automatische Auschecken
 Dieses Unterbereich Hintergrund Auschecken Szenarien, in denen die **Auschecken** Dialogfeld pro Benutzer nicht angezeigt **Tools**, **Optionen**, **Einstellungen für Quellcodeverwaltung** .

#### <a name="expected-behavior"></a>Es wird erwartet

- Nach dem Auschecken werden die Ziel-Dateien bzw. Ordner markiert, als im Versionsspeicher ausgecheckt.

- Der Versionsspeicher Attribute der sehen Sie sich an den richtigen Benutzer.

- Das Datum und Uhrzeit des das Auschecken stimmt (pro-Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Ordners kann geschrieben werden.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Automatische Auschecken einer Datei|1.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung** zu **Auschecken von Dateien automatisch in Bearbeitung**.<br />2.  Erstellen eines neuen Projekts mit einer Datei an.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Die Datei auschecken.|Datei wird automatisch ausgecheckt (ohne Benutzeroberfläche).|
|Automatische Auschecken für ein Projekt|1.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung** zu **Auschecken von Dateien automatisch in Bearbeitung**.<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Sehen Sie sich das Projekt.|Datei wird automatisch ausgecheckt (ohne Benutzeroberfläche).|

### <a name="case-3e-undo-check-out"></a>Groß-/Kleinschreibung 3e: Auschecken rückgängig machen
 **Rückgängig: Auschecken** dient zum Abbrechen einer Datei ausgecheckt, Status und zu überprüfen, ob Änderungen an der Datei vorgenommen.

#### <a name="expected-behavior"></a>Es wird erwartet

- Der Standardwert basiert darauf, dass des Benutzers **lokale Version Auschecken** festlegen. Wenn der Benutzer ausgewählt hat, um die lokale Version auszuchecken, ist die Standardeinstellung für "Auschecken rückgängig" immer wieder in den die Version, die ausgecheckt.

- Nach Annahme der rückgängig-, die Symbole in **Projektmappen-Explorer** aktualisiert werden, für die betroffenen Dateien und das Element wird aus entfernt die **Anstehende Eincheckvorgänge** Fenster.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Rückgängig: Auschecken einer Datei, die exklusiv ausgecheckt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Eine Datei exklusiv auschecken.<br />4.  Ändern Sie die Datei an.<br />5.  Rückgängig: Auschecken (**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**).|Allgemeine Erwartetes Verhalten.|
|Rückgängig: Auschecken einer Datei, die freigegeben ausgecheckt wird|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Sehen Sie sich eine freigegebene Datei.<br />4.  Ändern Sie die Datei an.<br />5.  Rückgängig: Auschecken (**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**).|Allgemeine Erwartetes Verhalten.|
|Rückgängig: Auschecken eines Projekts nach dem Hinzufügen von Dateien zum Projekt|1.  Erstellen eines neuen Projekts, und fügen Sie es zur quellcodeverwaltung hinzu.<br />2.  Sehen Sie sich das Projekt.<br />3.  Fügen Sie dem Projekt eine Datei.<br />4.  Rückgängig: Auschecken des Projekts.|Hinzugefügte Datei wird aus dem Projekt im Projektmappen-Explorer entfernt.<br /><br /> Projekt wird nicht mehr ausgecheckt.|
|Rückgängig: Auschecken eines Projekts nach dem Löschen von Dateien aus dem Projekt|1.  Erstellen eines neuen Projekts, und fügen Sie es zur quellcodeverwaltung hinzu.<br />2.  Sehen Sie sich das Projekt.<br />3.  Löschen Sie eine Datei aus dem Projekt ein.<br />4.  Rückgängig: Auschecken des Projekts.|Die Datei wurde gelöscht, die unter dem Projekt im Projektmappen-Explorer wird angezeigt.<br /><br /> Projekt wird nicht mehr ausgecheckt.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
