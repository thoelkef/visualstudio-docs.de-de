---
title: Änderungsprotokoll (Visual Studio-Tools für Unity, Mac) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/05/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d43542dc78c8bc0eaeb05e1a620edff7a88efa37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31084118"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Änderungsprotokoll (Visual Studio-Tools für Unity, Mac)
Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="1501"></a>1.5.0.1
 Veröffentlichung: 28.3.2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Im Unity-Projekt-Explorer wurde die Unterstützung für zusätzliche Vorlagen hinzugefügt.

## <a name="1500"></a>1.5.0.0
 Veröffentlichung: 21.3.2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Es wurde Unterstützung für das Erkennen und Anfügen von Android-Playern hinzugefügt, die über USB verbunden sind.

## <a name="1403"></a>1.4.0.3
 Veröffentlichung: 05.03.2018
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Es wurde Unterstützung für den neuen Projektgenerator in Unity 2018.1 hinzugefügt.

-   **Integration:**

    -   Ein Optionsbereich für dedizierte Einstellungen wurde hinzugefügt.

## <a name="1402"></a>1.4.0.2
 Veröffentlichung: 24.01.2018
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Projektgenerierung:**

    -   Erkennung von Mono-Version korrigiert.

-   **Integration:**

    -   Probleme bei Zeitabläufen mit 2018.1 und Plug-in-Aktivierung behoben.

    -   Es wurden Probleme mit Benachrichtigungen behoben, die beim Erkennen eines neuen Players angezeigt werden.

## <a name="1401"></a>1.4.0.1
 Veröffentlichung: 23.1.2018
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Es wurden Probleme mit dem Erweitern und Reduzieren von Ordnern durch Doppelklicken behoben.

## <a name="1400"></a>1.4.0.0
 Veröffentlichung: 13.12.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Unterstützung für .NET Standard wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

## <a name="1301"></a>1.3.0.1
 Veröffentlichung: 12.12.2017
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Indirekter Aufruf von EditorPrefs.GetBool, der den Inspektor beim Versuch beeinträchtigt, die Größe des Arrays zu ändern, korrigiert.

-   **Assistenten:**

    -   Aktualisieren des Roslyn-Kontexts vor dem Einfügen der Methode.

## <a name="1300"></a>1.3.0.0
 Veröffentlichung: 20.11.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Assistenten:**

    -   Der Assistent für das Implementieren von Unity-Meldungen wurde hinzugefügt.

    -   Es wurde Unterstützung für die neue Abschluss-API in Visual Studio für Mac 7.4 hinzugefügt.

## <a name="1200"></a>1.2.0.0
 Veröffentlichung: 23.10.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Debugger:**

    -   Es wurde Unterstützung für portierbare Debugsymboldateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Projektgenerierung:**

    -   Korrigiert: Eine zusätzliche DLL-Erweiterung wird dem Assemblydateinamen fälschlicherweise hinzugefügt.

    -   Erzwingen Sie nicht das Unity-Flag „AllowAttachedDebuggingOfEditor“, da der Standard jetzt TRUE ist.

## <a name="1103"></a>1.1.0.3
 Veröffentlichung: 23.10.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Projektgenerierung:**

    -   Zusätzliche Unterstützung für .NET 4.6-Profil.

## <a name="1102"></a>1.1.0.2
 Veröffentlichung: 8.8.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Debugger:**

    -   Starten Sie das Dialogfeld „An den Prozess anhängen“, wenn Sie nicht sicher sind, an welche Unity-Version angehängt werden soll.

-   **Projektgenerierung:**

    -   Aktivieren Sie immer den unsafe-Kompilierungsschalter, wenn Unity 5.6 verwendet wird.

## <a name="1101"></a>1.1.0.1
 Veröffentlichung: 20.7.2017
 
### <a name="new-features"></a>Neue Funktionen

-   **Integration:**

    -   Es wurde Unterstützung für lokalisierte Ressourcen hinzugefügt.

## <a name="1100"></a>1.1.0.0
 Veröffentlichung: 12.7.2017
 
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
 Veröffentlichung: 4.5.2017
 
### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Integration:**

    -   Es wurden Probleme bei der aktiven Nachverfolgung von Dokumenten bei hybriden und regulären Projekten behoben.

## <a name="1000"></a>1.0.0.0
 Veröffentlichung: 3.5.2017
