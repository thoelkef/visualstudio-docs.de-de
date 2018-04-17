---
title: 'Testbereich 3: Check Out rückgängig: Auschecken | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d769fdc52ac92053c258a3f82fa53cec5c56fa7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-3-check-outundo-checkout"></a>Testbereich 3: Auschecken / rückgängig: Auschecken
Dieser Bereich der quellcodeverwaltung für die Test-Plug-in behandelt, bearbeiten und Zurücksetzen der Elemente aus dem Versionsspeicher über die **Auschecken** und **Rückgängig: Auschecken** Befehle.  
  
 **Auschecken**: Markierungen ein Element im Versionsspeicher als ausgecheckt ändert die lokale Kopie für Lese-/Schreibzugriff.  
  
 **Rückgängig: Auschecken**: markiert ein Element im Versionsspeicher wie eingecheckt, vor dem Auschecken (je nach Optionen) zum lokalen Kopie zurückgesetzt.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### <a name="check-out"></a>Abreise:  
  
-   **Datei**, **Quellcodeverwaltung**, **Auschecken**.  
  
-   **Datei**, **Auschecken**.  
  
-   Klicken Sie im Kontextmenü **Auschecken**.  
  
-   Auschecken rückgängig: **Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**.  
  
## <a name="common-expected-behavior"></a>Allgemeine erwartet  
  
-   Die Ziel-Dateien und/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute das Auschecken, den richtigen Benutzernamen an.  
  
-   Uhrzeit und Datum des Auscheckens Richtigkeit (gemäß den Einstellungen des Benutzers).  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden finden bestimmte Testfälle zum Bereich "Test" Auschecken rückgängig: Auschecken / "".  
  
### <a name="case-3a-check-out"></a>Case-3a: Auschecken  
 Dieser Abschnitt konzentriert sich auf den Betrieb des Befehls Auschecken.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Überprüfen Sie, exklusive (festgestellte) ein Clientprojekt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Sehen Sie sich das gesamte Projekt ausschließlich (**Datei**, **Auschecken**).|Auschecken auftritt.|  
|Sehen Sie sich exklusiven (festgestellte), ein Dateisystem oder dem lokalen IIS-Webprojekt|1.  Legen Sie die Web-Server-Verbindung mit der Freigabe in der Datei **Tools**, **Optionen**, **Projekte**, **Web-Einstellungen**.<br />2.  Erstellen Sie ein Webprojekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Sehen Sie sich das gesamte Projekt ausschließlich (**Datei**, **Quellcodeverwaltung**, **Auschecken**).|Auschecken auftritt.|  
|Sehen Sie sich Projektmappenelemente in einer Projektmappe (neue Methode zum Behandeln von anderen Dateien)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Die Projektmappe Auschecken.<br />4.  Fügen Sie mehrere Projektmappenelemente hinzu.<br />5.  Überprüfen Sie in den neu hinzugefügten Elementen.<br />6.  Wählen Sie mehrere Projektmappenelemente.<br />7.  Sehen Sie sich die ausgewählten Elemente (klicken Sie im Kontextmenü **Auschecken**).|Ausgewählte Dateien werden ausgecheckt.|  
|Lokale Version auschecken (sofern-Plug-in unter dem Test dieses Feature unterstützt)|1.  Benutzer 1: Erstellen Sie ein Clientprojekt.<br />2.  Benutzer 1: Die Projektmappe zur quellcodeverwaltung hinzufügen.<br />3.  Benutzer 2: Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einen anderen Speicherort.<br />4.  Benutzer 2: Auschecken einer Datei ab.<br />5.  Benutzer 2: Ändern Sie die Datei.<br />6.  Benutzer 2: Überprüfen Sie in der Datei.<br />7.  Benutzer 1: Auschecken von lokalen Version der Datei (Überprüfen Sie die **lokale Version Auschecken** erweiterte Optionen in **Auschecken** Dialogfeld).|Lokale Version der Datei ist ausgecheckt.<br /><br /> Änderungen durch Benutzer 2 werden nicht auf Benutzer 1-Datei angewendet.|  
  
### <a name="case-3b-disconnected-check-out"></a>Fall 3 b: Auschecken getrennt  
 Im getrennten Modus ermöglicht Benutzern Maß Steuerelement-Unterstützung fortgesetzte Datenquellen, wenn nicht direkt an einen Versionsspeicher angefügt. Dies erfolgt, indem Sie alle relevanten Informationen über die eingetragenen Projektmappen und Projekte lokal zwischenspeichern.  
  
 Exklusives Auschecken Vorgänge kann nur auftreten, während einer Verbindung mit dem Speicher der quellcodeverwaltung. Freigegebenen Auschecken Vorgänge zu einem beliebigen Zeitpunkt ist möglich, ob verbunden oder getrennt. Aus diesem Grund Wenn getrennt aus dem Versionsspeicher nur die **überprüfen und freigegeben** (COS) Befehl aktiviert ist. Wenn Sie verbunden sind, **Rückgängig: Auschecken** ist deaktiviert, da die alte Version abgerufen werden kann, um vom Benutzer vorgenommene Änderungen zu ersetzen.  
  
 Wenn der Benutzer auf die Version erneut hergestellt speichern, die Zustände Auschecken aller eingetragenen Lösungen und Projekte synchronisiert. Dies hat die erforderlichen Updates in den Speicher für das Auschecken, die der Benutzer ausgeführt hat. Nachdem die Synchronisierung stattgefunden hat, kann der Benutzer weiterhin wie gewohnt (verbunden) arbeiten.  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Können keine **ausschließlich Out** Befehl, wenn Sie aus dem Versionsspeicher verbunden.  
  
-   Können keine **Rückgängig: Auschecken** Befehl, wenn Sie aus dem Versionsspeicher verbunden.  
  
-   **Freigegebene Auschecken** Befehl funktioniert.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Wenn Sie verbunden sind, eine Datei checken Sie aus und anschließend für die Synchronisierung|1.  Trennen ein kontrolliertes-Projekts mit Quellcodeverwaltung ändern (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**l).<br />2.  Eine Datei auschecken.<br />3.  Klicken Sie auf Auschecken (getrennt) im Dialogfeld "Warnung".<br />4.  Bearbeiten Sie die Datei.<br />5.  Verbinden Sie mithilfe des Dialogfelds für die Quellcodeverwaltung ändern.<br />6.  Neueste Version der bearbeitete Datei abrufen.|Allgemeine erwartet|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Fall 3c: Abfrage bearbeiten/Abfrage speichern (QEQS.)  
 Elemente in der quellcodeverwaltung für die Bearbeitung, Änderungen, nachverfolgt werden, und speichert auf Benutzer einfacher verwalten ihrer Dateien. Bei einem kontrollierten-Element, das "Einchecken" bearbeitet wird, fängt der versuchte bearbeiten QEQS ab und der Benutzer gefragt, ob er checkt die Datei zu bearbeiten möchte. Je nach **Tools**, **Optionen** Einstellungen, die der Benutzer ist entweder gezwungen, überprüfen Sie die Datei zum Bearbeiten auschecken oder möglicherweise Kopie im Arbeitsspeicher bearbeiten, und sehen Sie sich später gestattet werden. Wenn des Benutzers **Tools**, **Optionen** Einstellung ist nicht festgelegt werden, um das Auschecken im Dialogfeld anzuzeigen und zu einfach überprüfen Sie es aus, und klicken Sie dann wie der Benutzer seine bearbeiten hergestellt hat, die Datei automatisch ausgecheckt, wann immer möglich.  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Die Ziel-Dateien und/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute Auschecken des an den richtigen Benutzernamen an.  
  
-   Das Datum und Uhrzeit des Auschecken des Richtigkeit (gemäß den Einstellungen des Benutzers).  
  
-   Die lokale Kopie der Zieldatei oder des Ordners kann geschrieben werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Bearbeiten Sie die Textdatei, die eingecheckt wird|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** zu deaktiviert.<br />4.  Festlegen **Tools**, **Optionen**, **Quellcodeverwaltung**, **Aufforderung zum Auschecken** in der **beim Einchecken, werden Dateien bearbeitete** Kombinationsfeld.<br />5.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Aufforderung zum Auschecken** in die **Dateien werden beim Einchecken gespeichert** Kombinationsfeld.<br />6.  Text-Datei im Editor zu öffnen, bei dem Versuch, geben Sie den neuen Text in die Datei. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />7.  Klicken Sie auf **"Abbrechen"** in der **zum Bearbeiten auschecken** (Dialogfeld). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />8.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** zu aktiviert.<br />9. Öffnen Sie die Projektdatei im Editor, bei dem Versuch, geben Sie den neuen Text in der Datei. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />10. Klicken Sie auf **bearbeiten** in der **zum Bearbeiten auschecken** (Dialogfeld). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />11. Bearbeiten Sie die Textdatei, und versuchen Sie es speichern.|`Result of step 6:`<br /><br /> Sehen Sie sich für bearbeiten (Dialogfeld) wird angezeigt.<br /><br /> `Result of step 7:`<br /><br /> Die Datei wird nicht geändert.<br /><br /> `Result of step 9:`<br /><br /> Sehen Sie sich für bearbeiten (Dialogfeld) wird angezeigt.<br /><br /> `Result of step 10:`<br /><br /> Sie können die Projektdatei im Arbeitsspeicher bearbeiten.<br /><br /> `Result of step 11:`<br /><br /> Speichern wird auf das Auschecken auf Speichern (Dialogfeld).|  
|Bearbeiten einer Projektmappendatei, die eingecheckt wird|Wiederholen Sie die Schritte wie in früheren beschrieben zu testen, aber anstatt zu ändern, eine Textdatei, die Projektmappe durch Ändern der Eigenschaften ändern.|Identisch mit der vorherigen Tests|  
|Bearbeiten einer Projektdatei, die eingecheckt wird|Wiederholen Sie die Schritte wie in früheren beschrieben zu testen, aber anstatt zu ändern, eine Textdatei, Projekt geändert werden, indem Projekteigenschaften ändern.|Identisch mit der vorherigen Tests.|  
  
### <a name="case-3d-silent-check-out"></a>Fall 3d: Automatische Auschecken  
 Diese untergeordneten Bereich deckt Auschecken Szenarien, in dem die **Auschecken** Dialogfeld pro des Benutzers nicht angezeigt **Tools**, **Optionen**, **Einstellungen für Quellcodeverwaltung** .  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Die Ziel-Dateien und/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute Auschecken des an den richtigen Benutzernamen an.  
  
-   Das Datum und Uhrzeit des Auschecken des ist (gemäß den benutzereinstellungen) richtig.  
  
-   Die lokale Kopie der Zieldatei oder des Ordners kann geschrieben werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Automatische Auschecken einer Datei|1.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung** auf **Auschecken von Dateien automatisch auf Bearbeiten**.<br />2.  Erstellen Sie ein neues Projekt mit einer Datei.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Die Datei auschecken.|Datei automatisch ausgecheckt ist (ohne Benutzeroberfläche).|  
|Automatische Auschecken für ein Projekt|1.  Legen Sie **Tools**, **Optionen**, **Quellcodeverwaltung** auf **Auschecken von Dateien automatisch auf Bearbeiten**.<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Checken Sie das Projekt aus.|Datei automatisch ausgecheckt ist (ohne Benutzeroberfläche).|  
  
### <a name="case-3e-undo-check-out"></a>Case-3e: Auschecken rückgängig machen  
 **Rückgängig: Auschecken** wird verwendet, um "Abbrechen" einer Datei ausgecheckt, Status und zu vermeiden, in der Datei vorgenommenen Änderungen einchecken.  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Der Standardwert basiert auf des Benutzers **Auschecken lokaler Versionen** Einstellung. Wenn der Benutzer für die lokale Version auszuchecken ausgewählt wurde, ist die Standardeinstellung für das Auschecken rückgängig immer der ausgecheckten Version wiederherstellen.  
  
-   Nach Annahme der rückgängig-, die Symbole in **Projektmappen-Explorer** werden aktualisiert, für die betroffenen Dateien und das Element wird entfernt, von der **Anstehende Eincheckvorgänge** Fenster.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Rückgängig: Auschecken einer Datei, die exklusiv ausgecheckt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Eine Datei exklusiv auschecken.<br />4.  Ändern Sie die Datei an.<br />5.  Auschecken rückgängig machen (**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**).|Allgemeine erwartet.|  
|Rückgängig: Auschecken einer Datei, die freigegeben ausgecheckt ist|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Checken Sie eine freigegebene Datei aus.<br />4.  Ändern Sie die Datei an.<br />5.  Auschecken rückgängig machen (**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**).|Allgemeine erwartet.|  
|Rückgängig: Auschecken eines Projekts nach dem Hinzufügen von Dateien zum Projekt|1.  Erstellen eines neuen Projekts, und es zur quellcodeverwaltung hinzufügen.<br />2.  Checken Sie das Projekt aus.<br />3.  Fügen Sie dem Projekt eine Datei hinzu.<br />4.  Rückgängig: Auschecken des Projekts.|Hinzugefügte Datei wird aus dem Projekt im Projektmappen-Explorer entfernt.<br /><br /> Projekt ist nicht mehr ausgecheckt.|  
|Rückgängig: Auschecken eines Projekts nach dem Löschen von Dateien aus dem Projekt|1.  Erstellen eines neuen Projekts, und es zur quellcodeverwaltung hinzufügen.<br />2.  Checken Sie das Projekt aus.<br />3.  Löschen Sie eine Datei aus dem Projekt ein.<br />4.  Rückgängig: Auschecken des Projekts.|Gelöschte Datei wird unter dem Projekt im Projektmappen-Explorer angezeigt.<br /><br /> Projekt ist nicht mehr ausgecheckt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)