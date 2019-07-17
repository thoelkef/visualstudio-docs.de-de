---
title: Änderungsprotokoll (Visual Studio-Tools für Unity, Mac) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e5bc02948d410d465d7ac1be798ff17ebc5daaf9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821513"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Änderungsprotokoll (Visual Studio-Tools für Unity, Mac)

Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="2020"></a>2.0.2.0

Veröffentlichung: 2. April 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für die automatische Aktualisierung der Asset-Datenbank von Unity beim Speichern hinzugefügt. Dies ist standardmäßig aktiviert und löst beim Speichern eines Skripts in Visual Studio eine Neukompilierung auf der Unity-Seite aus. Sie können dieses Feature in „Tools\Optionen\Tools für Unity\AssetDatabase von Unity beim Speichern aktualisieren“ deaktivieren.

  - Unterstützung für das Festlegen der bevorzugten Unity-Installation für Offlinedokumentation hinzugefügt.

  - Kontextmenü für den neuen Editor hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Fehler bei Assemblyfilterung und Frameüberprüfung mit leeren Frames behoben.

## <a name="2011"></a>2.0.1.1
 Veröffentlichung: 26. März 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Vorübergehend ist Mono der standardmäßige und einzige verwendbare Debugger für dieses spezifische Release.

## <a name="2006"></a>2.0.0.6

Veröffentlichung: 26. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für „An Unity anfügen und wiedergeben“ hinzugefügt.

## <a name="2005"></a>2.0.0.5

Veröffentlichung: 20. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Projektgenerierung:**

  - Beibehalten externer Eigenschaften bei Verarbeitung der Projektmappendatei.

## <a name="2004"></a>2.0.0.4

Veröffentlichung: 5. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - ScriptableObject-API aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Namespaces aus Vorlagen entfernt.

## <a name="2003"></a>2.0.0.3
 Veröffentlichung: 5. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Projektgenerierung:**

  - Öffentliche und serialisierte Felder rufen keine Warnungen mehr hervor. Wir haben die Compilerwarnungen CS0649 und IDE0051 in Unity-Projekten, die diese Nachrichten erstellt haben, automatisch unterdrückt.

- **Integration:**

  - Aufforderung zum Anfügen an eine bestimmte Instanz, wenn mehrere Unity-Prozesse ausgeführt werden.

- **Auswertung:**

  - Unterstützung für lokale Funktionen hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Das Lesen von benutzerdefinierten Attributen für benannte Argumente wurde korrigiert, wenn alte Protokollversionen verwendet wurden.

## <a name="2002"></a>2.0.0.2

Veröffentlichung: 4. Februar 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - MonoBehaviour-API aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Korrektur des Festlegens primitiver Werte im Debugger.

## <a name="2001"></a>2.0.0.1

Veröffentlichung: 4. Dezember 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrektur der Selbstkapselung des Installationspakets.

## <a name="2000"></a>2.0.0.0
 Veröffentlichung: 4. Dezember 2018

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Der Unity-Debugger für Mac wurde durch den gleichen grundlegenden Unity-Debugger der Windows-Version ersetzt.

  - NRefactory zugunsten von Roslyn für die Auswertung von Ausdrücken ersetzt.

  - Unterstützung für Zeiger hinzugefügt: Dereferenzieren, Umwandeln und Zeigerarithmetik (Unity 2018.2+ und die neue Runtime sind dafür erforderlich).

  - Unterstützung für Arrayzeigeransicht (wie in C++). Nehmen Sie einen Zeigerausdruck und fügen Sie dann ein Komma und die Anzahl der Elemente hinzu, die Sie anzeigen möchten.

  - Unterstützung für asynchrone Konstrukte hinzugefügt.

  - Unterstützung für Pseudovariablen (Ausnahme und die Objekt-IDs) hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Auswertung von Ausdrücken mit fehlerhaften oder nicht unterstützten Ausdrücken korrigiert.

## <a name="1700"></a>1.7.0.0

Veröffentlichung: 13. November 2018

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Dem Dialogfeld „Anfügen“ wurden weitere Informationen zum Client hinzugefügt (IP-Adresse, Computername).

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Es wurde ein Deadlock in der Bibliothek behoben, die zur Kommunikation mit der Debuggerengine von Unity verwendet wurde, wodurch Visual Studio oder Unity nicht mehr reagiert haben (insbesondere, wenn auf „Attach to Unity“ geklickt oder das Spiel neu gestartet wurde).

- **Integration:**

  - Ein Fehler bei der Aktivierung des Unity-Plug-Ins wurde behoben, der auftrat, wenn ein anderer Standard-Editor ausgewählt wurde.

  - Die Erstellung von Unity-Dateivorlagen wurde behoben.

## <a name="1602"></a>1.6.0.2

Veröffentlichung: 24. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Rollback der Problemumgehung für ein Leistungsproblem von Unity, da Unity dieses behoben hat.

## <a name="1601"></a>1.6.0.1

Veröffentlichung: 10. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Ein Problem bei der Unterstützung für die Codeeinfärbung für Shader wurde behoben.

## <a name="1600"></a>1.6.0.0

Veröffentlichung: 26. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Assistenten:**

  - Ein Schreibfehler in der OnApplicationFocus-Meldung wurde korrigiert.

- **Projektgenerierung:**

  - Vorübergehende Problemumgehung für ein Leistungsproblem von Unity: Zwischenspeichern von MonoIslands beim Generieren von Projekten.

  - Konvertieren Sie keine portablen PDB-Dateien mehr in MDB-Dateien, wenn Sie die neue Unity-Runtime verwenden.

## <a name="1502"></a>1.5.0.2

Veröffentlichung: 18. April 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für die Vervollständigung von Shader-Code wurde hinzugefügt.

  - Unterstützung für das Umschalten von Kommentaren in Shader-Dateien wurde hinzugefügt.

## <a name="1501"></a>1.5.0.1

Veröffentlichung: 28. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Im Unity-Projekt-Explorer wurde die Unterstützung für zusätzliche Vorlagen hinzugefügt.

## <a name="1500"></a>1.5.0.0

Veröffentlichung: 21. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für das Erkennen und Anfügen von Android-Playern hinzugefügt, die über USB verbunden sind.

## <a name="1403"></a>1.4.0.3

Veröffentlichung: 5. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Projektgenerierung:**

  - Es wurde Unterstützung für den neuen Projektgenerator in Unity 2018.1 hinzugefügt.

- **Integration:**

  - Ein Optionsbereich für dedizierte Einstellungen wurde hinzugefügt.

## <a name="1402"></a>1.4.0.2

Veröffentlichung: 24. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Projektgenerierung:**

  - Erkennung von Mono-Version korrigiert.

- **Integration:**

  - Probleme bei Zeitabläufen mit 2018.1 und Plug-in-Aktivierung behoben.

  - Es wurden Probleme mit Benachrichtigungen behoben, die beim Erkennen eines neuen Players angezeigt werden.

## <a name="1401"></a>1.4.0.1

Veröffentlichung: 23. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Probleme mit dem Erweitern und Reduzieren von Ordnern durch Doppelklicken behoben.

## <a name="1400"></a>1.4.0.0

Veröffentlichung: 13. Dezember 2017

### <a name="new-features"></a>Neue Funktionen

- **Projektgenerierung:**

  - Unterstützung für .NET Standard wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

## <a name="1301"></a>1.3.0.1

Veröffentlichung: 12. Dezember 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Indirekter Aufruf von EditorPrefs.GetBool, der den Inspektor beim Versuch beeinträchtigt, die Größe des Arrays zu ändern, korrigiert.

- **Assistenten:**

  - Aktualisieren des Roslyn-Kontexts vor dem Einfügen der Methode.

## <a name="1300"></a>1.3.0.0

Veröffentlichung: 20. November 2017

### <a name="new-features"></a>Neue Funktionen

- **Assistenten:**

  - Der Assistent für das Implementieren von Unity-Meldungen wurde hinzugefügt.

  - Es wurde Unterstützung für die neue Abschluss-API in Visual Studio für Mac 7.4 hinzugefügt.

## <a name="1200"></a>1.2.0.0

Veröffentlichung: 23. Oktober 2017

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Es wurde Unterstützung für portierbare Debugsymboldateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Projektgenerierung:**

  - Korrigiert: Eine zusätzliche DLL-Erweiterung wird dem Assemblydateinamen fälschlicherweise hinzugefügt.

  - Erzwingen Sie nicht das Unity-Flag „AllowAttachedDebuggingOfEditor“, da der Standard jetzt TRUE ist.

## <a name="1103"></a>1.1.0.3

Veröffentlichung: 23. Oktober 2017

### <a name="new-features"></a>Neue Funktionen

- **Projektgenerierung:**

  - Zusätzliche Unterstützung für .NET 4.6-Profil.

## <a name="1102"></a>1.1.0.2

Veröffentlichung: 8. August 2017

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Starten Sie das Dialogfeld „An den Prozess anhängen“, wenn Sie nicht sicher sind, an welche Unity-Version angehängt werden soll.

- **Projektgenerierung:**

  - Aktivieren Sie immer den unsafe-Kompilierungsschalter, wenn Unity 5.6 verwendet wird.

## <a name="1101"></a>1.1.0.1

Veröffentlichung: 20. Juli 2017

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für lokalisierte Ressourcen hinzugefügt.

## <a name="1100"></a>1.1.0.0

Veröffentlichung: 12. Juli 2017

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für das Anhängen an Player und Editors über das Fenster „An den Prozess anhängen“ hinzugefügt.

- **Projektgenerierung:**

  - Fehlerhafte Assembly-Namensverweise bei mcs.rsp Dateien behoben.

  - assembly.json-Kompilierungseinheiten werden nun unterstützt.

  - Fehlerhafte define-Anweisungen bei API-Ebenen wurden behoben.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Eine auf Shader bezogene Fehlermeldung bei der Kompilierung wurde entfernt.

## <a name="1001"></a>1.0.0.1

Veröffentlichung: 4. Mai 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Probleme bei der aktiven Nachverfolgung von Dokumenten bei hybriden und regulären Projekten behoben.

## <a name="1000"></a>1.0.0.0

Veröffentlichung: 3. Mai 2017
