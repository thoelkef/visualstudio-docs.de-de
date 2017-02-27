---
title: "Testbereich 3: Check Out r&#252;ckg&#228;ngig: Auschecken | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins, Auschecken"
  - "Source Control-Plug-ins "Auschecken rückgängig""
  - "Beim Auschecken der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Source Control "Auschecken rückgängig" [Visual Studio SDK]"
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Testbereich 3: Auschecken / Auschecken r&#252;ckg&#228;ngig machen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Datenquellen\-Steuerelement Test\-Plug\-in Hierunter bearbeiten und Zurücksetzen der Elemente aus dem Versionsspeicher über die **Auschecken** und **Rückgängig: Auschecken** Befehle.  
  
 **Auschecken**: markiert ein Element im Versionsspeicher als ausgecheckt ändert der lokale Kopie mit Lese\-\/Schreibzugriff.  
  
 **Rückgängig: Auschecken**: kennzeichnet ein Element im Versionsspeicher markiert, wird die lokale Kopie Zustand vor dem Auschecken \(je nach Optionen\) zurückgesetzt.  
  
## Befehl Menüzugriff  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development\-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### Abreise:  
  
-   **Datei**, **Quellcodeverwaltung**, **Auschecken**.  
  
-   **Datei**, **Auschecken**.  
  
-   Klicken Sie im Kontextmenü **Auschecken**.  
  
-   Auschecken rückgängig: **Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**.  
  
## Allgemeine erwartet  
  
-   Die Ziel\-Dateien und\/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute das Auschecken an den richtigen Benutzer.  
  
-   Uhrzeit und Datum des Auscheckvorgangs von stimmen \(pro Einstellungen des Benutzers\).  
  
## Testfälle  
 Im folgenden sind bestimmte Testfälle für den Testbereich Auschecken\/rückgängig: Auschecken.  
  
### Fall 3a: Auschecken  
 Dieser Abschnitt konzentriert sich auf den Betrieb des mit dem Befehl Auschecken.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Überprüfen Sie, exklusive \(festgestellte\) ein Clientprojekt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Das gesamte Projekt exklusiv auschecken \(**Datei**, **Auschecken**\).|Auschecken auftritt.|  
|Exklusiv \(festgestellte\) checken Sie aus, ein Dateisystem oder lokalen IIS\-Webprojekt|1.  Legen Sie die Web\-Server\-Verbindung die Freigabe in eine Datei **Tools**, **Optionen**, **Projekte**, **Web\-Einstellungen**.<br />2.  Erstellen Sie ein Webprojekt.<br />3.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />4.  Das gesamte Projekt exklusiv auschecken \(**Datei**, **Quellcodeverwaltung**, **Auschecken**\).|Auschecken auftritt.|  
|Sehen Sie sich Projektmappenelemente in einer Projektmappe \(neue Methode für die Behandlung von anderen Dateien\)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Checken Sie die Projektmappe aus.<br />4.  Mehrere Projektmappenelemente hinzufügen.<br />5.  Überprüfen Sie in alle neu hinzugefügten Elemente.<br />6.  Wählen Sie mehrere Projektmappen\-Elemente.<br />7.  Sehen Sie sich die ausgewählten Elemente \(klicken Sie im Kontextmenü **Auschecken**\).|Ausgewählte Dateien werden ausgecheckt.|  
|Lokale Version auschecken \(wenn plug\-in unter Test dieses Feature unterstützt\)|1.  Benutzer 1: Erstellen Sie ein Clientprojekt.<br />2.  Benutzer 1: Die Projektmappe zur Versionskontrolle hinzufügen.<br />3.  Benutzer 2: Öffnen Sie die Projektmappe aus Datenquellen\-Steuerelement an einen anderen Speicherort.<br />4.  Benutzer 2: Auschecken einer Datei ab.<br />5.  Benutzer 2: Ändern Sie die Datei.<br />6.  Benutzer 2: Überprüfen Sie in der Datei.<br />7.  Benutzer 1: Auschecken der lokalen Version der Datei \(Überprüfen Sie die **lokale Version Auschecken** erweiterte Option in **Auschecken** Dialogfeld\).|Lokale Version der Datei ist ausgecheckt.<br /><br /> Änderungen von Benutzer 2 gelten nicht für Benutzer 1\-Datei.|  
  
### Fall 3: Auschecken getrennt  
 Im getrennten Modus kann Benutzer gewisse fortgesetzten Quelle Steuerelements unterstützen, wenn nicht direkt an einen Versionsspeicher angefügt. Dies erfolgt, indem alle relevanten Informationen über die eingetragenen Projektmappen und Projekte lokal zwischengespeichert.  
  
 Exklusives Auschecken Vorgänge kann nur erfolgen, während der Verbindung mit dem Speicher der quellcodeverwaltung. Freigegebenen Auschecken Operationen kann zu einem beliebigen Zeitpunkt ausgeführt, ob verbunden oder getrennt. Aus diesem Grund bei Trennung von der Versionsspeicher nur die **Überprüfen und freigegeben** \(COS\) Befehl aktiviert ist. Offline, **Rückgängig: Auschecken** ist deaktiviert, da die alte Version abgerufen werden kann, um vom Benutzer vorgenommenen Änderungen zu ersetzen.  
  
 Stellt der Benutzer auf die Version speichern, die Checkout\-Status aller eingetragenen Lösungen und Projekte synchronisiert. Dies führt die erforderlichen Updates in den Speicher für das Auschecken, die der Benutzer ausgeführt hat. Nach die Synchronisierung eingetreten ist, kann der Benutzer weiterhin wie gewohnt arbeiten \(verbunden\).  
  
#### Es wird erwartet  
  
-   Können keine **ausschließlich überprüfen** Befehl aus dem Versionsspeicher offline.  
  
-   Können keine **Rückgängig: Auschecken** Befehl aus dem Versionsspeicher offline.  
  
-   **Freigegebenen Auschecken** \-Befehl funktioniert.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Offline, Auschecken einer Datei herstellen, dann für die Synchronisierung|1.  Trennen einer gesteuerten Projekt Quellcodeverwaltung ändern im Dialogfeld \(**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**l\).<br />2.  Eine Datei auschecken.<br />3.  Klicken Sie auf Auschecken \(getrennt\) im Dialogfeld "Warnung".<br />4.  Bearbeiten Sie die Datei.<br />5.  Verbinden Sie mit dem Dialogfeld Datenquellen\-Steuerelement ändern.<br />6.  Neueste Version der bearbeiteten Datei abrufen.|Allgemeine erwartet|  
  
### Fall 3c: Abfrage bearbeiten\/Abfrage speichern \(QEQS.\)  
 Elemente unter dem Datenquellen\-Steuerelement für die Bearbeitung, Änderungen, nachverfolgt, und speichert Benutzer problemlos zu verwalten, ihre Dateien. Bei einem gesteuerten\-Element, das "Einchecken" bearbeitet wird, fängt der versuchte bearbeiten QEQS ab und fordert den Benutzer, wenn er die Datei zum Bearbeiten auschecken möchte. Je nach **Tools**, **Optionen** Einstellungen der Benutzer wird entweder die gezwungen, überprüfen Sie die Datei um bearbeiten bzw. berechtigt, auf die Kopie im Arbeitsspeicher bearbeiten, und sehen Sie sich später. Wenn des Benutzers **Tools**, **Optionen** Einstellung ist nicht festgelegt, um das Dialogfeld Auschecken anzuzeigen und zu es einfach überprüfen, und wie der Benutzer seine bearbeiten vornimmt, die Datei automatisch ausgecheckt, wenn möglich.  
  
#### Es wird erwartet  
  
-   Die Ziel\-Dateien und\/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute das Auschecken an den richtigen Benutzer.  
  
-   Das Datum der Prüfung, und die stimmen \(pro Einstellungen des Benutzers\).  
  
-   Die lokale Kopie der Zieldatei oder des Ordners ist nicht schreibgeschützt.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Bearbeiten Sie die Textdatei, die eingecheckt wird|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Legen Sie **Tools**, **Optionen**, **Source Control**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** zu deaktiviert.<br />4.  Legen Sie **Tools**, **Optionen**, **Source Control**, **Aufforderung zum Auschecken** in der **Wenn eingecheckte Dateien bearbeitet werden** im Kombinationsfeld.<br />5.  Legen Sie **Tools**, **Optionen**, **Source Control**, **Aufforderung zum Auschecken** in der **beim Einchecken der Dateien gespeichert werden** im Kombinationsfeld.<br />6.  Text\-Datei im Editor zu öffnen, bei dem Versuch, geben Sie neues Text in die Datei. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />7.  Klicken Sie auf **Abbrechen** in den **zum Bearbeiten auschecken** \(Dialogfeld\). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />8.  Legen Sie **Tools**, **Optionen**, **Source Control**, **Dateien bearbeitet werden, während auf dem Datenträger schreibgeschützt zulassen** Option.<br />9. Öffnen Sie die Datei in Editor, bei dem Versuch, geben Sie neues Text in der Datei. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />10. Klicken Sie auf **Bearbeiten** in den **zum Bearbeiten auschecken** \(Dialogfeld\). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />11. Bearbeiten Sie die Textdatei, und versuchen Sie, es zu speichern.|`Result of step 6:`<br /><br /> Sehen Sie sich im Dialogfeld zum Bearbeiten angezeigt.<br /><br /> `Result of step 7:`<br /><br /> Die Datei bleibt unverändert.<br /><br /> `Result of step 9:`<br /><br /> Sehen Sie sich im Dialogfeld zum Bearbeiten angezeigt.<br /><br /> `Result of step 10:`<br /><br /> Sie können die Projektdatei im Arbeitsspeicher bearbeiten.<br /><br /> `Result of step 11:`<br /><br /> Speichern wird auf das Auschecken auf Speichern.|  
|Bearbeiten einer Projektmappendatei, die eingecheckt werden|Wiederholen Sie die Schritte wie in vorherigen beschrieben zu testen, aber anstatt zu ändern, eine Textdatei, die Projektmappe durch Ändern der Eigenschaften ändern.|Wie der vorherige test|  
|Bearbeiten einer Projektdatei, die eingecheckt werden|Wiederholen Sie die Schritte wie in vorherigen beschrieben zu testen, aber anstelle eine Textdatei ändern, ändern Projekt durch Ändern der Projekteigenschaften.|Entspricht der vorherige Test.|  
  
### Case\-3d: Automatische Auschecken  
 Dieses Gebiet behandelt Auschecken Szenarien, in denen die **Auschecken** pro Benutzer im Dialogfeld nicht angezeigt **Tools**, **Optionen**, **Source Control Settings**.  
  
#### Es wird erwartet  
  
-   Die Ziel\-Dateien und\/oder Ordner werden nach dem Auschecken als im Versionsspeicher ausgecheckt markiert.  
  
-   Der Versionsspeicher Attribute das Auschecken an den richtigen Benutzer.  
  
-   Das Datum und Uhrzeit des Auschecken ist korrekt \(pro Einstellungen des Benutzers\).  
  
-   Die lokale Kopie der Zieldatei oder des Ordners ist nicht schreibgeschützt.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Automatische Auschecken einer Datei|1.  Legen Sie **Tools**, **Optionen**, **Source Control** auf **Auschecken von Dateien automatisch auf Bearbeiten**.<br />2.  Erstellen Sie ein neues Projekt mit einer Datei.<br />3.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />4.  Die Datei auschecken.|Datei automatisch ausgecheckt wird \(keine Benutzeroberfläche\).|  
|Automatische Auschecken für ein Projekt|1.  Legen Sie **Tools**, **Optionen**, **Source Control** auf **Auschecken von Dateien automatisch auf Bearbeiten**.<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />4.  Checken Sie das Projekt aus.|Datei automatisch ausgecheckt wird \(keine Benutzeroberfläche\).|  
  
### Case\-3e: Auschecken rückgängig machen  
 **Rückgängig: Auschecken** brechen einer Datei ausgecheckt, Status und zu überprüfen, ob Änderungen an der Datei vorgenommen werden.  
  
#### Es wird erwartet  
  
-   Der Standardwert basiert auf des Benutzers **lokale Version Auschecken** festlegen. Wenn der Benutzer ausgewählt hat, um die lokale Version auszuchecken, ist die Standardeinstellung für das Auschecken rückgängig, immer auf die Version ausgecheckt zurückzusetzen.  
  
-   Nach Annahme der rückgängig\-, die Symbole in **Projektmappen\-Explorer** werden aktualisiert, für die betroffenen Dateien und das Element wird entfernt, von der **Anstehende Eincheckvorgänge** Fenster.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Rückgängig: Auschecken einer Datei, die exklusiv ausgecheckt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Eine Datei exklusiv auschecken.<br />4.  Ändern Sie die Datei.<br />5.  Auschecken rückgängig machen \(**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**\).|Allgemeine erwartet.|  
|Rückgängig: Auschecken einer Datei, die freigegeben ausgecheckt ist|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Checken Sie eine freigegebene Datei aus.<br />4.  Ändern Sie die Datei.<br />5.  Auschecken rückgängig machen \(**Datei**, **Quellcodeverwaltung**, **Rückgängig: Auschecken**\).|Allgemeine erwartet.|  
|Rückgängig: Auschecken eines Projekts nach dem Hinzufügen von Dateien zum Projekt|1.  Erstellen eines neuen Projekts, und es zur Versionskontrolle hinzufügen.<br />2.  Checken Sie das Projekt aus.<br />3.  Fügen Sie dem Projekt eine Datei hinzu.<br />4.  Rückgängig: Auschecken des Projekts.|Hinzugefügte Datei wird aus dem Projekt im Projektmappen\-Explorer entfernt.<br /><br /> Projekt ist nicht mehr ausgecheckt.|  
|Rückgängig: Auschecken eines Projekts nach dem Löschen von Dateien aus dem Projekt|1.  Erstellen eines neuen Projekts, und es zur Versionskontrolle hinzufügen.<br />2.  Checken Sie das Projekt aus.<br />3.  Löschen Sie eine Datei aus dem Projekt.<br />4.  Rückgängig: Auschecken des Projekts.|Gelöschte Datei wird unter dem Projekt im Projektmappen\-Explorer angezeigt.<br /><br /> Projekt ist nicht mehr ausgecheckt.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)