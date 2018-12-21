---
title: Änderungsprotokoll (Visual Studio-Tools für Unity, Mac) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/13/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0b641c9dd1fe797fc036a6ece893ad61fc52ff87
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027236"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Änderungsprotokoll (Visual Studio-Tools für Unity, Mac)
Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="1700"></a>1.7.0.0
 Veröffentlichung: 13. November 2018

### <a name="new-features"></a>Neue Funktionen

-   **Debugger:**

    -   Dem Dialogfeld „Anfügen“ wurden weitere Informationen zum Client hinzugefügt (IP-Adresse, Computername).

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Debugger:**

     -   Es wurde ein Deadlock in der Bibliothek behoben, die zur Kommunikation mit der Debuggerengine von Unity verwendet wurde, wodurch Visual Studio oder Unity nicht mehr reagiert haben (insbesondere, wenn auf „Attach to Unity“ geklickt oder das Spiel neu gestartet wurde).
     
-   **Integration:**

     -   Ein Fehler bei der Aktivierung des Unity-Plug-Ins wurde behoben, der auftrat, wenn ein anderer Standard-Editor ausgewählt wurde.
     
     -   Die Erstellung von Unity-Dateivorlagen wurde behoben.

## <a name="1602"></a>1.6.0.2
 Veröffentlichung: 24. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

     -   Rollback der Problemumgehung für ein Leistungsproblem von Unity, da Unity dieses behoben hat.
     
## <a name="1601"></a>1.6.0.1
 Veröffentlichung: 10. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

     -   Ein Problem bei der Unterstützung für die Codeeinfärbung für Shader wurde behoben.
     
## <a name="1600"></a>1.6.0.0
 Veröffentlichung: 26. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Assistenten:**

    -   Ein Schreibfehler in der OnApplicationFocus-Meldung wurde korrigiert.

-   **Projektgenerierung:**

     -   Vorübergehende Problemumgehung für ein Leistungsproblem von Unity: Zwischenspeichern von MonoIslands beim Generieren von Projekten.
     
     -   Konvertieren Sie keine portablen PDB-Dateien mehr in MDB-Dateien, wenn Sie die neue Unity-Runtime verwenden.
     
## <a name="1502"></a>1.5.0.2
 Veröffentlichung: 18. April 2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Unterstützung für die Vervollständigung von Shader-Code wurde hinzugefügt.
    
    -   Unterstützung für das Umschalten von Kommentaren in Shader-Dateien wurde hinzugefügt.

## <a name="1501"></a>1.5.0.1
 Veröffentlichung: 28. März 2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Im Unity-Projekt-Explorer wurde die Unterstützung für zusätzliche Vorlagen hinzugefügt.

## <a name="1500"></a>1.5.0.0
 Veröffentlichung: 21. März 2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Es wurde Unterstützung für das Erkennen und Anfügen von Android-Playern hinzugefügt, die über USB verbunden sind.

## <a name="1403"></a>1.4.0.3
 Veröffentlichung: 5. März 2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Es wurde Unterstützung für den neuen Projektgenerator in Unity 2018.1 hinzugefügt.

-   **Integration:**

    -   Ein Optionsbereich für dedizierte Einstellungen wurde hinzugefügt.

## <a name="1402"></a>1.4.0.2
 Veröffentlichung: 24. Januar 2018
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Projektgenerierung:**

    -   Erkennung von Mono-Version korrigiert.

-   **Integration:**

    -   Probleme bei Zeitabläufen mit 2018.1 und Plug-in-Aktivierung behoben.

    -   Es wurden Probleme mit Benachrichtigungen behoben, die beim Erkennen eines neuen Players angezeigt werden.

## <a name="1401"></a>1.4.0.1
 Veröffentlichung: 23. Januar 2018
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Es wurden Probleme mit dem Erweitern und Reduzieren von Ordnern durch Doppelklicken behoben.

## <a name="1400"></a>1.4.0.0
 Veröffentlichung: 13. Dezember 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Unterstützung für .NET Standard wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

## <a name="1301"></a>1.3.0.1
 Veröffentlichung: 12. Dezember 2017
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Indirekter Aufruf von EditorPrefs.GetBool, der den Inspektor beim Versuch beeinträchtigt, die Größe des Arrays zu ändern, korrigiert.

-   **Assistenten:**

    -   Aktualisieren des Roslyn-Kontexts vor dem Einfügen der Methode.

## <a name="1300"></a>1.3.0.0
 Veröffentlichung: 20. November 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Assistenten:**

    -   Der Assistent für das Implementieren von Unity-Meldungen wurde hinzugefügt.

    -   Es wurde Unterstützung für die neue Abschluss-API in Visual Studio für Mac 7.4 hinzugefügt.

## <a name="1200"></a>1.2.0.0
 Veröffentlichung: 23. Oktober 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Debugger:**

    -   Es wurde Unterstützung für portierbare Debugsymboldateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Projektgenerierung:**

    -   Korrigiert: Eine zusätzliche DLL-Erweiterung wird dem Assemblydateinamen fälschlicherweise hinzugefügt.

    -   Erzwingen Sie nicht das Unity-Flag „AllowAttachedDebuggingOfEditor“, da der Standard jetzt TRUE ist.

## <a name="1103"></a>1.1.0.3
 Veröffentlichung: 23. Oktober 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Zusätzliche Unterstützung für .NET 4.6-Profil.

## <a name="1102"></a>1.1.0.2
 Veröffentlichung: 8. August 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Debugger:**

    -   Starten Sie das Dialogfeld „An den Prozess anhängen“, wenn Sie nicht sicher sind, an welche Unity-Version angehängt werden soll.

-   **Projektgenerierung:**

    -   Aktivieren Sie immer den unsafe-Kompilierungsschalter, wenn Unity 5.6 verwendet wird.

## <a name="1101"></a>1.1.0.1
 Veröffentlichung: 20. Juli 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Es wurde Unterstützung für lokalisierte Ressourcen hinzugefügt.

## <a name="1100"></a>1.1.0.0
 Veröffentlichung: 12. Juli 2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Es wurde Unterstützung für das Anhängen an Player und Editors über das Fenster „An den Prozess anhängen“ hinzugefügt.

-   **Projektgenerierung:**

    -   Fehlerhafte Assembly-Namensverweise bei mcs.rsp Dateien behoben.

    -   assembly.json-Kompilierungseinheiten werden nun unterstützt.    

    -   Fehlerhafte define-Anweisungen bei API-Ebenen wurden behoben.    

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Eine auf Shader bezogene Fehlermeldung bei der Kompilierung wurde entfernt.

## <a name="1001"></a>1.0.0.1
 Veröffentlichung: 4. Mai 2017
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Es wurden Probleme bei der aktiven Nachverfolgung von Dokumenten bei hybriden und regulären Projekten behoben.

## <a name="1000"></a>1.0.0.0
 Veröffentlichung: 3. Mai 2017
