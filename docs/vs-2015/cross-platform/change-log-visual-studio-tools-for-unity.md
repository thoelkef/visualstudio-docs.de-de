---
title: Änderungsprotokoll (Visual Studio-Tools für Unity) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: e21fdbd55ddfe6088a6b8a7ff4127a05b1fa4ce1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791965"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Änderungsprotokoll (Visual Studio-Tools für Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="23"></a>2.3
 Veröffentlichung: 14.7.2016

### <a name="new-features"></a>Neue Funktionen

-   **Allgemein:**

    -   Hinzufügung einer Option, um Unity-Konsolenprotokolle in der Fehlerliste von Visual Studio zu deaktivieren.

    -   Hinzufügung einer Option, mit der generierte Projekteigenschaften geändert werden können.

-   **Debugger:**

    -   Hinzufügung von Text-, XML-, HTML- und JSON-Zeichenfolgenschnellansichten.

-   **Assistenten:**

    -   Hinzufügung fehlender MonoBehaviors.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Allgemein:**

    -   Behebung eines Konflikts mit ReSharper, der verhinderte, dass Steuerelemente innerhalb von Visual Studio-Einstellungen angezeigt werden.

    -   Behebung eines Konflikts mit Xamarin, der in einigen Fällen das Debugging verhinderte.

-   **Debugger:**

    -   Es wurde ein Problem behoben, das in Visual Studio beim Debuggen zu einem Code Freeze geführt hat.

    -   Behebung eines Problems mit Funktionshaltepunkten in Visual Studio 2015.

    -   Behebung mehrerer Probleme bei der Ausdrucksauswertung.

## <a name="22"></a>2.2
 Veröffentlichung: 04.02.2016

### <a name="new-features"></a>Neue Funktionen

-   **Assistenten:**

    -   Intelligente Suche wurde im **"MonoBehaviours" implementieren** -Assistenten hinzugefügt.

    -   Die Assistenten wurden so geändert, dass sie kontextberücksichtigend sind. Beispielsweise sind NetworkBehavior-Nachrichten nur verfügbar, wenn mit einem NetworkBehavior gearbeitet wird.

    -   In den Assistenten wurde Unterstützung für NetworkBehavior-Nachrichten hinzugefügt.

-   **Benutzeroberfläche:**

    -   Eine Option zum Konfigurieren der Sichtbarkeit von MonoBehavior-Nachrichten wurde hinzugefügt.

    -   Es wurden die Visual Studio-Eigenschaftenseiten entfernt, die für Unity-Projekte keine Bedeutung haben.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Projektgenerierung:**

    -   Verweise auf UnityEngine und UnityEditor für Unity 4.6 wurden korrigiert.

    -   Die Generierung von Projektdateien wurde für den Fall korrigiert, dass Unity unter OS X ausgeführt wird.

    -   Die Verarbeitung von Projektnamen, die Nummernzeichen (#) enthalten, wurde korrigiert.

    -   Generierte Projekte wurden auf C# 4 beschränkt.

-   **Debugger:**

    -   Es wurde ein Problem mit der Auswertung von Ausdrücken behoben, wenn eine Unity-Koroutine debuggt wird.

    -   Es wurde ein Problem behoben, das in Visual Studio beim Debuggen zu einem Code Freeze geführt hat.

-   **Benutzeroberfläche:**

    -   Es wurde eine Inkompatibilität behoben, die mit der Visual Studio-Erweiterung [Tabs Studio](https://tabsstudio.com/) aufgetreten ist.

-   **Installer:**

    -   Unterstützung für computerweite Installation von VSTU (Installation für alle Benutzer) durch Erstellen von HKLM-Registrierungseinträgen.

    -   Es wurden Probleme behoben, die beim Deinstallieren von VSTU aufgetreten sind, wenn für mehrere verschiedene Versionen von Visual Studio dieselbe Version von VSTU installiert war. Zum Beispiel, wenn sowohl VSTU **2015** 2.1.0.0 als auch VSTU **2013** 2.1.0.0 installiert waren.

## <a name="21"></a>2.1
 Veröffentlichung: 08.09.2015

### <a name="new-features"></a>Neue Funktionen

-   Unterstützung für Unity 5.2

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Anzeigen von Menüelementen in Unity < 4.2

-   Es wird keine Fehlermeldung mehr angezeigt, wenn Intellisense-XML-Dateien von Visual Studio gesperrt werden.

-   Verarbeiten bedingter <\<When Changed>>-Haltepunkte, wenn das bedingte Argument kein boolescher Wert ist.

-   Korrektur der Verweise auf Assemblys von UnityEngine und UnityEditor für Windows Store-Apps.

-   Ein Fehler bei der schrittweisen Ausführung des Debuggers wurde behoben: schrittweise Ausführung nicht möglich, allgemeine Ausnahme.

-   Korrektur der Trefferanzahl-Haltepunkte in Visual Studio 2015.

## <a name="20"></a>2.0
 Veröffentlichung: 20.07.2015

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Unity-Integration:**

    -   Korrektur der Konvertierung von Debugsymbolen, die mit Visual Studio 2015 beim Importieren einer DLL und ihrer Debugsymbole (PDB) erstellt werden.

    -   Beim Importieren einer DLL und ihrer Debugsymbole (PDB) werden immer MDB-Dateien generiert, außer wenn auch eine MDB-Datei bereitgestellt wird.

    -   Korrektur der Verunreinigung des Unity-Projektverzeichnisses mit einem Verzeichnis „obj“.

    -   Korrektur der Generierung von Verweisen auf „System.Xml.Link“ und „System.Runtime.Serialization“.

    -   Zusätzliche Unterstützung für mehrere Abonnenten der API-Hooks zum Erstellen der Projektdatei.

    -   Es wird immer eine vollständige Projektdatei erstellt, auch wenn eine der zu generierenden Dateien gesperrt ist.

    -   Zusätzliche Unterstützung für *-Platzhalter im Erweiterungsfilter beim Festlegen der in das C#-Projekt einzuschließenden Dateien.

-   **Visual Studio-Integration:**

    -   Korrektur eines Kompatibilitätsproblems mit den Productivity Power Tools.

    -   Korrektur der Generierung von MonoBehaviors im Zusammenhang mit Deklarationen von Ereignissen und Delegaten.

-   **Debugger:**

    -   Korrektur des potenziellen Einfrierens beim Debuggen.

    -   Korrektur eines Problems, aufgrund dessen lokale Variablen in bestimmten Stapelrahmen nicht angezeigt werden.

    -   Korrektur der Überprüfung leerer Arrays.

## <a name="20-preview-2"></a>2.0 Preview 2
 Veröffentlichung: 02.04.2015

### <a name="new-features"></a>Neue Funktionen

-   **Unity-Projekt-Explorer:**

    -   Automatisches Umbenennen der Klasse beim Umbenennen einer Datei im Unity-Projekt-Explorer (siehe das Dialogfeld **Optionen** ).

    -   Automatisches Auswählen neu erstellter Skripts im Unity-Projekt-Explorer.

    -   Nachverfolgen des aktiven Skripts im Unity-Projekt-Explorer (siehe das Dialogfeld **Optionen** ).

    -   Duale Synchronisierung des Projektmappen-Explorers von Visual Studio (siehe **Optionen** Dialogfeld).

    -   Übernahme von Visual Studio-Symbolen im Unity-Projekt-Explorer.

-   **Debugger:**

    -   Auswählen des aktiven Debugziels in einer Liste gespeicherter oder zuletzt verwendeter Debugziele (siehe das Dialogfeld **Optionen** ).

    -   Erstellen von Funktionshaltepunkten für MonoBehavior-Methoden und deren Anwendung auf mehrere MonoBehavior-Klassen.

    -   Unterstützung der "Make Objekt"-ID im Debugger.

    -   Unterstützung der Trefferanzahl für Haltepunkte im Debugger.

    -   Unterstützung von Unterbrechung bei Ausnahme im Debugger (experimentell. Siehe das Dialogfeld **Optionen** ).

    -   Unterstützung der Erstellung von Objekten und Arrays beim Auswerten von Ausdrücken im Debugger.

    -   Unterstützung von NULL-Vergleichen bei der Auswertung von Ausdrücken im Debugger.

    -   Herausfiltern veraltete Member im Überwachungsfenster des Debuggers.

-   **Installer:**

    -   Optimierte Registrierung von Visual Studio-Tools für Unity-Erweiterungen.

    -   Installation des Visual Studio-Tools für Unity-Pakets für Unity 5.

-   **Dokumentation:** Verbesserte Leistung bei der Dokumentationserstellung.

-   **Assistenten:** Unterstützung neuer MonoBehavior-Methoden für Unity 4.6 und Unity 5.

-   **Unity:** Nachschlagen unsicherer Kennzeichen und benutzerdefinierter Definitionen in RSP-Dateien während der Erstellung der Projektdatei.

-   **Benutzeroberfläche:** Visual Studio-Tools für Unity-Dialogfeld **Optionen** in Visual Studio hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   **Unity-Projekt-Explorer:**

    -   Der Unity-Projekt-Explorer wird aktualisiert, nachdem Dateien im Projektmappen-Explorer von Visual Studio verschoben oder umbenannt wurden.

    -   Auswahlen werden beim Umbenennen von Dateien im Unity-Projekt-Explorer beibehalten.

    -   Das automatische Erweitern und Reduzieren wird verhindert, wenn im Unity-Projekt-Explorer auf Dateien doppelgeklickt wird.

    -   Es wird sichergestellt, dass neu ausgewählte Dateien im Unity-Projekt-Explorer angezeigt werden.

-   **Debugger:**

    -   Ein mögliches Einfrieren von Visual Studio beim Auswerten von Ausdrücken im Debugger wird verhindert.

    -   Es wird sichergestellt, dass Methodenaufrufe in der richtigen Domäne im Debugger erfolgen.

-   **Unity:**

    -   Korrektur des Speicherorts von UnityVS.OpenFile bei Unity 5.

    -   Korrektur des Speicherorts von "pdb2mdb" bei Unity 5.

    -   Eine mögliche Ausnahme während der Erstellung der Projektdatei wird verhindert.

    -   Ein mögliches Einfrieren bei Ausführung von Unity unter OSX wird verhindert.

    -   Interne Ausnahmen werden behandelt.

    -   Unity-Konsolenprotokolle werden an die Visual Studio-Fehlerliste gesendet.

-   **Dokumentation:** Ordnungsgemäße Dokumentationserstellung für die neue Unity-Dokumentation.

-   **Projekt:** Verschieben und Umbenennen von Unity-Dateien vom Typ „.meta“ bei Bedarf, sogar in Ordnern.

-   **Assistenten:** Korrektur der Reihenfolge der Parameter der MonoBehavior-Methode beim Generieren von Code.

-   **Benutzeroberfläche:** Unterstützung von Visual Studio-Designs für das Kontextmenü und Symbole.

## <a name="20-preview"></a>2.0 Preview
 Veröffentlichung: 12.11.2014

### <a name="new-features"></a>Neue Funktionen

-   Unterstützung für Visual Studio 2015.

-   Färbung von Code für Unity-Shader in Visual Studio 2015.

-   Optimierung der Darstellung von Werten beim Debuggen:

    -   Bessere Visualisierung für Arraylisten, Listen, Hashtabellen und Wörterbücher.

    -   Anzeigen nicht öffentlicher und statischer Member als Kategorien in Überwachungs- und lokalen Ansichten.

    -   Verbesserte Anzeige der "SerializedProperty" von Unity, sodass nur das für die Eigenschaft gültige Wertfeld ausgewertet wird.

    -   Unterstützung von "DebuggerDisplayAttribute" für Klassen und Strukturen.

    -   Unterstützung für "DebuggerTypeProxyAttribute".

-   Einfügung von MonoBehaviour-Methoden mithilfe unserer Assistenten unter Berücksichtigen der Codierkonventionen der Benutzer.

-   Implementierung von Unterstützung für Textvorlagen zur Kompilierzeit in mit UnityVS generierten Projekten.

-   Implementieren von Unterstützung für ResX-Ressourcen in mit UnityVS generierten Projekten.

-   Unterstützung des Öffnens von Shadern in Visual Studio aus Unity.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Bereinigung von Sockets vor dem Starten des Spiels in Unity, nachdem "Anfügen" und "Wiedergeben" in Visual Studio ausgelöst wurden. Dies beseitigt einige Probleme mit der Stabilität der Verbindung zwischen Unity und VS bei Verwenden von "Anfügen" und "Wiedergeben".

-   Vermeiden des Aufrufens von Methoden auf der Debuggeroberfläche der Skript-Engine von Unity, die anfällig für das Einfrieren von Unity sind. Dadurch wird das Einfrieren von Unity beim Anfügen des Debuggers behoben.

-   Korrektur der Anzeige von Aufruflisten, wenn keine Symbole verfügbar sind.

-   Registrierung des Rückrufprotokolls, nur wenn unbedingt erforderlich.

## <a name="192"></a>1.9.2
 Veröffentlichung: 09.10.2014

### <a name="new-features"></a>Neue Funktionen

-   Verbesserung der Erkennung von Unity-Playern.

-   Bei Verwenden unserer Dateiöffnungsanwendung übergibt Unity nun die Zeilennummer und den Dateinamen.

-   Standardmäßiges Zurückgreifen auf die Unity-Onlinedokumentation, wenn es keine lokale Dokumentation gibt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Beseitigung potenzieller Unity-Abstürze, wenn ein Haltepunkt nach dem Neuladen einer Domäne erreicht wird.

-   Beseitigung von in der Unity-Konsole angezeigten Ausnahmen, wenn unsere Fenster "Konfiguration" oder "Info" nach dem Neuladen einer Domäne geschlossen werden.

-   Korrektur der Erkennung von lokal ausgeführtem 64-Bit-Unity.

-   Korrektur der Filterung von MonoBehaviour-Methoden nach Unity-Version im Assistenten.

-   Korrektur eines Fehlers, bei dem alle Objekte den Projektdateien hinzugefügt wurden, wenn der Erweiterungsfilter leer war.

## <a name="191"></a>1.9.1
 Veröffentlichung: 22.09.2014

### <a name="new-features"></a>Neue Funktionen

-   Optimierung des Bindens von Haltepunkten an Speicherorte von Quellcode.

-   Unterstützung für überladene Methoden in der Ausdrucksauswertung des Debuggers.

-   Unterstützung für das Boxing von Primitiven und Werttypen in der Ausdrucksauswertung des Debuggers.

-   Unterstützung für das Neuerstellen der C#-Umgebung für lokale Variablen beim Debuggen anonymer Methoden.

-   Löschen und Umbenennen von META-Dateien beim Löschen oder Umbenennen von Dateien in Visual Studio.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur bei der Behandlung von Visual Studio-Themen. Zuvor konnten Dialogfelder bei schwarzen Designs leer erscheinen.

-   Korrektur des Einfrierens von Unity beim Verbinden des Debuggers, während Unity die Neukompilierung durchführt.

-   Korrektur von Haltepunkten beim Debuggen von Remote-Editoren oder -Playern, die auf einem anderen System kompiliert wurden.

-   Vermeidung eines möglichen Visual Studio-Absturzes, wenn ein Haltepunkt erreicht wird.

-   Korrektur der Bindung von Haltepunkten, um zu vermeiden, dass Haltepunkte als entladen angezeigt werden.

-   Korrektur der Verarbeitung des Variablenbereichs im Debugger zur Vermeidung von Livevariablen, die außerhalb des gültigen Bereichs liegen.

-   Korrektur des Nachschlagens statischer Member in der Ausdrucksauswertung des Debuggers.

-   Korrektur der Anzeige von Typen in der Ausdrucksauswertung des Debuggers dahingehend, dass statische Fehler und Eigenschaften angezeigt werden.

-   Korrektur bei der Erstellung einer Projektmappe, wenn Unity-Projektnamen Sonderzeichen enthalten, die Visual Studio nicht zulässt (Verbindungsproblem 948666).

-   Korrektur des Visual Studio Tools für Unity-Pakets dahingehend, dass das Senden von Konsolenereignissen sofort beendet wird, nachdem die Option deaktiviert wurde (Verbindungsproblem 933357).

-   Korrektur der Erkennung von Verweisen, um in den von UnityVS generierten Projekten Verweise auf neue APIs wie "UnityEngine.UI" ordnungsgemäß neu zu erstellen.

-   Korrektur des Installers dahingehend, dass Visual Studio vor der Installation geschlossen wird, um beschädigte Installationen zu vermeiden.

-   Korrektur des Installers dahingehend, dass Unity-Verweisassemblys als ordnungsgemäße eigenständige Komponente installiert werden, die von allen Versionen von VSTU gemeinsam genutzt werden.

-   Korrektur beim Öffnen von Skripts mit VSTU in 64-Bit-Versionen von Unity.

## <a name="19"></a>1.9
 Veröffentlichung: 29.07.2014

### <a name="new-features"></a>Neue Funktionen

-   Im Fenster "Unity-Debugger anfügen" Hinzufügung der Möglichkeit zum Eingeben benutzerdefinierter Angaben für IP-Adressen und Ports für das Debugging.

-   Hinzufügung der Konfigurationsoption zum Festlegen der Ausführung von Unity im Hintergrund oder nicht.

-   Hinzufügung einer Konfigurationsoption zum Generieren von Projektmappen- und Projektdateien oder ausschließlich von Projektdateien.

-   Startziel: Auswählen von "An Unity anfügen" oder "An Unity anfügen und wiedergeben"

-   Anzeige mehrdimensionaler Arrays im Debugger.

-   Behandlung neuer Debuggingports für den Unity-Player.

-   Behandlung von Verweisen auf neue Unity-Assemblys wie Unity 4.6 GUI-Assemblys.

-   Zerlegung von Abschlüssen zum ordnungsgemäßen Anzeigen lokaler Variablen beim Debugging.

-   Zerlegung generierter Iteratorvariablen in Argumente beim Debugging.

-   Beibehaltung des Zustand des Unity-Projekt-Explorers nach dem Neuladen eines Projekts.

-   Hinzufügung eines Befehls zum Synchronisieren des Unity-Projekt-Explorers mit dem aktuellen Dokument.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur bedingter Haltepunkte, deren Bedingungen festgelegt werden, bevor der Debugger gestartet wird.

-   Korrektur von Verweisen auf "UnityEngine", um Warnungen zu vermeiden.

-   Korrektur der Analyse von Versionen für Unity-Betaversionen.

-   Korrektur eines Problems, bei dem Variablen nicht im Fenster mit den lokalen Variablen angezeigt werden, wenn ein Haltepunkt erreicht oder Code schrittweise ausgeführt wird.

-   Korrektur von QuickInfos für Variablen in Visual Studio 2013.

-   Korrektur der Erstellung der IntelliSense-Dokumentation für Unity 4.5.

-   Korrektur der Unity-/Visual Studio-Kommunikation nach dem Neuladen einer Domäne (Wiedergeben/Anhalten in Unity).

-   Korrektur bei der Verarbeitung von Teilen von Visual Studio-Themen.

> [!IMPORTANT]
>  C# ist die vorherrschende Sprache im Unity-Ökosystem. Die neuen Beispielobjekte sind in C# geschrieben. Die Unity-Dokumentation wurde standardmäßig auf C# umgestellt. UnityScript und Boo werden nicht mehr unterstützt, um den Schwerpunkt ganz auf die C#-Umgebung zu legen. Demzufolge basieren VSTU-Lösungen nun ausschließlich auf C# und können viel schneller geladen werden.

## <a name="182"></a>1.8.2
 Veröffentlichung: 07.01.2014

### <a name="new-features"></a>Neue Funktionen

-   Umgehung eines Problems auf der Vermittlungsschicht in der Skript-Engine von Unity für Mavericks für die Remoteerkennung von Editoren.

-   Behandlung neuer Ports zum Erkennen von Unity-Remoteplayern.

-   Verweis der UnityEngine-Assembly spezifisch für das aktuelle Buildziel.

-   Hinzufügung einer Einstellung zum Filtern von Dateien für die Einbeziehung in generierte Projekte.

-   Hinzufügung einer Einstellung zum Deaktivieren des Sendens von Konsolenprotokollen an die Visual Studio-Fehlerliste. Dies ist hilfreich, wenn Sie PlayMaker oder Console Pro verwenden, da möglicherweise in Unity nur ein Rückruf für das Empfangen von Konsolenprotokollen registriert ist.

-   Hinzufügung einer Einstellung zum Deaktivieren der Generierung von MDB-Debugsymbolen. Dies ist hilfreich, wenn Sie die MDB selbst generieren.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur einer Regression beim Öffnen von Dateien in Visual Studio aus Unity > = 4.2 (Verlust von IntelliSense).

-   Korrektur unserer VS-Dialogfelder zur Unterstützung benutzerdefinierter Designs.

-   Korrektur für das Schließen des Kontextmenüs der UPE.

-   Verhinderung eines Absturzes in Unity, wenn die versionsspezifisch generierte Assembly nicht mehr synchron ist.

## <a name="181"></a>1.8.1
 Veröffentlichung: 21.11.2013

### <a name="new-features"></a>Neue Funktionen

-   Korrektur der MonoBehaviour-Assistenten mit Unity 4.3-APIs.

-   MonoBehaviour-Assistenten filtern Unity-APIs abhängig von der Version, die Sie verwenden.

-   Hinzufügung eines Verweises auf "System.Xml.Linq" zu den Projekten für Unity > 4.1.

-   Verbesserung unserer Aufrufe an "Debug.Log", die jetzt nicht mehr den Anfang des StackTrace in der Meldung enthalten.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur eines Fehlers, der die Standardbehandlung von JavaScript-Dateien in Visual Studio beeinträchtigen würde.

-   Korrektur eines in VS angezeigten weißen Pixels (dieses Mal aber wirklich).

-   Korrektur des Löschens der Assembly "UnityVS.VersionSpecific", wenn sie durch einen SCM als schreibgeschützt gekennzeichnet ist.

-   Korrektur von Ausnahmen beim Erstellen von Sockets im UnityVS-Paket.

-   Korrektur eines Absturzes in Visual Studio beim Laden vorhandener Bilder aus Visual Studio-Assemblys.

-   Korrektur eines Fehlers bei der Generierung von "UnityVS.VersionSpecific" für Quellbuilds von Unity.

-   Korrektur eines möglichen Einfrierens beim Öffnen eines Sockets im Unity-Paket.

-   Korrektur der Behandlung eines Unity-Projekts mit einem Bindestrich (-) im Namen.

-   Korrektur beim Öffnen von Skripts zum Vermeiden der Verwechslung der ALT+TAB-Reihenfolge für Unity 4.2 und höher.

## <a name="180"></a>1.8.0
 Veröffentlichung: 24.09.2013

### <a name="new-features"></a>Neue Funktionen

-   Drastisch verbesserte Verbindungsgeschwindigkeit für den Debugger.

-   Automatisches Behandeln der Navigation zu Datei und Zeile für Unity 4.2 und höher.

-   Bedingte Haltepunkte.

-   Der Projektdateigenerator verarbeitet jetzt T4-Vorlagen.

-   Aktualisierung von MonoBehavior-Assistenten mit neuen APIs.

-   IntelliSense-Dokumentation in C# für Unity-Typen.

-   Auswertung arithmetischer und logischer Ausdrücke.

-   Bessere Erkennung von Remote-Editoren für die Remotedebuggingvorschau.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur eines Fehlers, der nach dem Trennen des Debuggers zu einem Threadverlust in Visual Studio führen würde.

-   Korrektur eines in Visual Studio angezeigten weißen Pixels.

-   Korrektur der Verarbeitung von Klicks auf das Statusleistensymbol.

-   Korrektur der Generierung von Verweisen bei Assemblys im Ordner "Plug-Ins".

-   Korrektur der Erstellung von Sockets aus dem UnityVS-Paket im Fall von Ausnahmen.

-   Korrektur der Erkennung neuer Versionen von UnityVS.

-   Korrektur der Eingabeaufforderung der Lizenzverwaltung, wenn die Lizenz abgelaufen ist.

-   Korrektur eines Fehlers, der im VS-Fenster " Debugger an Prozess anfügen" eine leere Prozessliste verursachen würde.

-   Korrektur der Änderung boolescher Werte in der lokalen Ansicht.

## <a name="122"></a>1.2.2
 Veröffentlichung: 09.07.2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Verarbeitung vollständig qualifizierter Namen in der Ausdrucksauswertung.

-   Korrektur des Einfrierens im Zusammenhang mit der Ausnahmebehandlung, bei der die Unity-Skript-Engine uns falsche StackFrame-Daten sendet.

-   Korrektur des Buildprozesses für Webziele.

-   Korrektur eines Fehlers, der auftreten kann, wenn Visual Studio gestartet wird und sich eine gelöschte Datei in der Liste der Dateien befindet, die beim Start geöffnet werden sollen.

-   Korrektur von "UnityVS.OpenFile" für die Verarbeitung von Nicht-Skriptdateien, wie z. B. kompilierte Shader.

-   Wir verweisen jetzt aus allen C#-Projekten auf "Boo.Lang" und "UnityScript.Lang".

-   Korrektur der Generierung von Verweisen in Projekten, wenn das Projekt Sonderzeichen enthält.

-   Umgehung eines VS-Problems, bei dem Methodenaufrufe an verworfene Projekte mehrere Meldungen vom Typ "NullReferenceException" auslösen.

-   Korrektur der Verarbeitung von Unity 4.2 Beta-Assemblys.

## <a name="121"></a>1.2.1
 Veröffentlichung: 09.04.2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der lokalen Bereitstellung von Unity-Assemblys für die Codevervollständigung bei einem E/A-Fehler (z. B. schreibgeschützte oder von Visual Studio gesperrte Dateien).

-   Korrektur einer Regression, bei der beim Öffnen eines Skripts in Unity der Fokus nicht auf der Datei liegt, die bereits in Visual Studio geöffnet wurde.

-   Korrektur eines Leistungsproblems bei der neuen Ausnahmebehandlung.

-   Korrektur der Bindung von Haltepunkten in einigen externen DLLs.

## <a name="12"></a>1.2
 Veröffentlichung: 25.03.2013

### <a name="new-features"></a>Neue Funktionen

-   Drastisch verbesserte Verbindungsgeschwindigkeit für den Debugger.

-   Optimierter Unity-Projekt-Explorer für größere Projekte.

-   Berücksichtigung der Visual Studio-Einstellungen für das Unterbrechen (oder nicht) bei behandelten und nicht behandelten Ausnahmen.

-   Berücksichtigung der Visual Studio-Einstellung für das Aufrufen von "ToString" für lokale Variablen.

-   Hinzufügung des neuen Menüs "Debug -> Unity-Debugger anfügen", mit dem Sie Unity-Player debuggen können.

-   Beibehalten benutzerdefinierter Projekte, die der UnityVS-Projektmappe bei Generierung der Projektmappendatei hinzugefügt werden.

-   Hinzufügung der neuen Tastenkombination STRG+ALT+M -> STRG+H, um die Unity-Dokumentation für den Unity-Funktion oder den Unity-Member an der Position der Einfügemarke anzuzeigen.

-   Berücksichtigung von Compilerantwortdateien (.rsp) beim Kompilieren von Visual Studio aus.

-   Zerlegung vom Compiler generierter Typen, um Variablen anzuzeigen, wenn Generatormethoden dem Debugging unterzogen werden.

-   Vereinfachung des Remotedebuggens, da für Unity kein freigegebener Ordner mehr konfiguriert werden muss. Sie können jetzt aus Windows auf das Unity-Projekt zugreifen.

-   Installation eines benutzerdefinierten Unity-Profil als standardmäßiges .NET-Zielprofil. Dies behebt alle falsch positiven Ergebnisse, die ReSharper anzeigen könnte.

-   Umgehung eines Unity-Skript-Engine-Fehlers, damit der Debugger bei nicht ordnungsgemäß registrierten Threads nicht unterbricht.

-   Überarbeitung der Dateiöffnungsfunktion zum Vermeiden einer Racebedingung, bei der VS vorgab, eine Datei öffnen zu können, es aber bei der Anforderung zum Öffnen der Datei zu einem Absturz kam.

-   UnityVS fordert nun das Aktualisieren des Builds an, wenn VS den Build für das Projekt erstellt, und nicht mehr beim Speichern der Datei.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur unseres benutzerdefinierten .NET-Profils.

-   Korrektur der Designintegration, wodurch unsere Probleme mit dem dunklen Visual Studio 2012-Design behoben werden.

-   Korrektur der Quick Behavior-Verknüpfung in Visual Studio 2012.

-   Korrektur eines Steppingproblems, das beim Debuggen und dann auftreten kann, wenn ein Nicht-Hauptthread auf einen Haltepunkt trifft.

-   Korrektur der UnityScript- und Boo-Vervollständigung von Typaliasnamen wie z. B. "int".

-   Korrektur einer Ausnahme beim Schreiben einer neuen UnityScript- oder Boo-Zeichenfolge.

-   Korrektur von Ausnahmen in Unity-Menüs, wenn eine Projektmappe nicht geladen wurde.

-   Korrektur von Bug UVS-48: Bei der Eingabe doppelter Anführungszeichen wird manchmal ein Fehler erzeugt, durch den alle Funktionen unterbrochen werden (Codevervollständigung, Syntaxhervorhebung usw.).

-   Fehler UVS-46 behoben: Doppelt geöffnete Skriptdatei (UnityScript) beim Klicken auf die Fehlerliste von Visual Studio.

-   Fehler UVS-42 behoben: Unity-Konnektivitätslogo in der Statusleiste verarbeitet keine Mausereignisse in VS 2012.

-   Fehler UVS-44 behoben: STRG+UMSCHALT+Q in VS 2012 für Quick MonoBehaviours nicht verfügbar.

-   Fehler UVS-40 behoben: Im Unity-Projekt-Explorer ausgewählte Elemente sind unlesbar, wenn das Fenster im „dunklen“ VS2012-Design inaktiv ist.

-   Fehler UVS-39 behoben: Fehler beim Ausstellen von Token für Escapezeichenfolgen.

-   Fehler UVS-35 behoben: Aufrufen von „ToString“ für Objekte beim Untersuchen von Variablen.

-   Fehler UVS-27 behoben: Inkonsistenz beim Fenster „Gehe zu Symbol“ mit „dunklem“ Design in VS2012.

-   Fehler UVS-11 behoben: Lokale Elemente in Coroutinen.

## <a name="11--beta-release"></a>1.1 – Betaversion
 Veröffentlichung: 09.10.2014

## <a name="1013"></a>1.0.13
 Veröffentlichung: 21.01.2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur einer Visual Studio-Blockade, die auftreten kann, wenn die zu debuggende Komponente ungültige Threadereignisse sendet. Dies passiert meist beim Debuggen einer Unity-Remoteprojekts unter OSX.

-   Korrektur einer Visual Studio-Blockade, die auftreten kann, wenn der Debugger aufgrund einer Ausnahme heruntergefahren wird.

-   Korrektur unserer MonoBehavior-Hilfsprogramme, wenn sich ein C#-MonoBehavior in einem Namespace befindet.

-   Korrektur von QuickInfos für den Debugger für UnityScript in Visual Studio 2012.

-   Korrektur der Projekterstellung, wenn von Unity aus nur Debugkonstanten geändert werden.

-   Korrektur der Tastaturnavigation im Unity-Projekt-Explorer.

-   Korrektur der farbigen UnityScript-Kennzeichnung für mit Escapezeichen versehene Zeichenfolgen.

-   Korrektur unserer Dateiöffnungsfunktion zur besseren Ermittlung des Projektnamens bei Verwendung außerhalb von Unity. Dies ist erforderlich, wenn der Benutzer in Unity eine Dateiöffnungsfunktion eines Drittanbieters verwendet, die an UnityVS delegiert.

-   Korrektur der Verarbeitung langer Meldungen, die von Unity an UnityVS gesendet werden. Zuvor konnten lange Meldungen unseren Meldungsteil von UnityVS zum Absturz bringen. Die Folge war, dass UnityVS manchmal eine Datei aus Unity nicht öffnen konnte.

## <a name="1012"></a>1.0.12
 Veröffentlichung: 03.01.2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur einer Visual Studio-Blockade, die erfolgen kann, wenn Visual Studio einen Haltepunkt gelöscht hat.

-   Korrektur eines Fehlers, bei dem einige Haltepunkte nicht getroffen werden, nachdem Unity Spielskripts neu kompiliert hat.

-   Korrektur des Debuggers dahingehend, dass Visual Studio ordnungsgemäß benachrichtigt wird, wenn Haltepunkte aufgehoben wurden.

-   Korrektur eines Registrierungsproblems, das den Visual Studio-Debugger am Debuggen systemeigener Programme hindern könnte.

-   Korrektur einer Ausnahme, die auftreten könnte, wenn UnityScript- und Boo-Ausdrücke ausgewertet werden.

-   Korrektur einer Regression, bei der beim Ändern der .NET-API-Ebene in Unity keine Aktualisierung der Projektdateien ausgelöst würde.

-   Korrektur eines API-Fehlers, bei dem Benutzercode nicht am Handler des Protokollrückrufs teilnehmen kann.

## <a name="1011"></a>1.0.11
 Veröffentlichung: 28.11.2012

### <a name="new-features"></a>Neue Funktionen

-   Offizielle Unterstützung von Unity 4.

-   Bearbeitung von Skripts im Unity-Projekt-Explorer.

-   Integration in das Visual Studio-Fenster "Navigieren zu".

-   Analyse der Info-Konsolenmeldung, damit Sie beim Klicken auf die Fehlerliste zum ersten Stackframe mit Symbolen gelangen.

-   Hinzufügung einer [API](../cross-platform/customize-project-files-created-by-vstu.md) , damit Benutzer an der Projekterstellung teilnehmen können.

-   Hinzufügung einer [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) , damit Benutzer am Protokollrückruf teilnehmen können.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur einer Regression im Hintergrund von Unity-Projekt-Explorer in Visual Studio 2012.

-   Korrektur der Projekterstellung für Benutzer des vollständigen .NET-Profils.

-   Korrektur der Projekterstellung für Benutzer des Ziels "Web".

-   Korrektur der Projekterstellung, indem die Kompilierungssymbole DEBUG und TRACE wie bei Unity einbezogen werden.

-   Korrektur eines Absturzes bei Verwendung von Sonderzeichen in unserem Symbolfenster "Gehe zu".

-   Korrektur eines Absturzes, wenn wir unser Symbol nicht in die Statusleiste von Visual Studio einfügen können.

## <a name="1010"></a>1.0.10
 Veröffentlichung: 09.10.2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur des Hintergrunds von Unity-Projekt-Explorer in Visual Studio 2010.

-   Korrektur eines Einfrierens von Visual Studio, das auftreten konnte, wenn UnityVS versuchte, den Debugger an ein Unity-Projekt anzufügen, dessen Debuggeroberfläche zuvor abgestürzt war.

-   Korrektur eines Einfrierens von Visual Studio, das auftreten konnte, wenn ein Haltepunkt festgelegt wurde und das Neuladen einer AppDomain erfolgte.

-   Korrektur, wie Assemblys aus Unity abgerufen werden, um das Sperren von Dateien und Verwechseln des Unity-Buildprozesses zu vermeiden.

## <a name="109"></a>1.0.9
 Veröffentlichung: 03.10.2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der Projekterstellung, wenn das Unity-Projekt tatsächliche JavaScript-Objekte enthält.

-   Korrektur der Fehlerbehandlung bei der Ausdrucksauswertung.

-   Korrektur beim Festlegen neuer Werte für Felder von Werttypen.

-   Korrektur möglicher Nebeneffekte bei Bewegen des Mauszeigers über Ausdrücke im Code-Editor.

-   Korrektur, wie Typen in geladenen Assemblys für die Ausdrucksauswertung durchsucht werden.

-   Fehler UVS-21 behoben: Auswertung der Zuweisung zu Unity-Objekten hat keine Auswirkung.

-   Fehler UVS-21 behoben: Ungültiger Zeiger beim Auswerten eines Methodenaufrufs in der Unity-Math-API.

## <a name="108"></a>1.0.8
 Veröffentlichung: 26.09.2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur des Abrufs des Pfads durch unsere Skriptöffnungsfunktion, um sicherzustellen, dass sie sowohl Visual Studio als auch die Skripts öffnen kann.

-   Korrektur eines Fehlers mit Haltepunkten, die während der aktiven Debugsitzung erstellt wurden und eine Blockade von Visual Studio verursachen konnten.

-   Korrektur, wie UnityVS in Visual Studio 2010 registriert wird.

## <a name="107"></a>1.0.7
 Veröffentlichung: 14.09.2012

### <a name="new-features"></a>Neue Funktionen

-   Unterstützung von Visual Studio 2012.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der Erstellung von Editor- und Plug-In-Projektdateien entsprechend dem Unity-Verhalten.

-   Korrektur der Übersetzung von PDB-Symbolen für Unity 4.

> [!IMPORTANT]
>  Durch die Unterstützung für Visual Studio 2012 mussten wir einige Dateien umbenennen und andere verschieben. Das UnityVS-Paket zum Importieren von Unity heißt jetzt für Visual Studio 2010 bzw. Visual Studio 2012 entweder UnityVS 2010 oder UnityVS 2012. Diese Version erfordert auch, dass die UnityVS-Projektdateien neu generiert werden.

## <a name="106---internal-build"></a>1.0.6 – Interner Build
 Veröffentlichung: 12.09.2012

## <a name="105"></a>1.0.5
 Veröffentlichung: 10.09.2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der Erstellung von Projektdateien, wenn Skripts oder Shader ein ungültiges XML-Zeichen enthielten.

-   Korrektur der Erkennung von Unity-Instanzen, wenn Unity mit dem Asset-Server verbunden war. Dadurch wurden Fehler beim Öffnen von Dateien aus Unity und bei der automatischen Verbindung von Visual Studio-Debuggers ausgelöst.

## <a name="104"></a>1.0.4
 Veröffentlichung: 05.09.2012

### <a name="new-features"></a>Neue Funktionen

-   Automatische Konvertierung von Debugsymbolen in Unity.

     Wenn sich in Ihrem Ordner "Asset" eine .NET-DLL-Assembly mit der zugehörigen PDB-Datei befindet, müssen Sie die Assembly einfach erneut importieren. Daraufhin konvertiert UnityVS die PDB-Datei in eine Debugsymboldatei, die die Unity-Skript-Engine versteht. Sie können anschließend Ihre .NET-Assemblys aus UnityVS schrittweise ausführen.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur eines UnityVS-Absturzes während des Debuggens, der von Unity-internen Methoden oder Eigenschaften ausgelöst wurde.

## <a name="103"></a>1.0.3
 Veröffentlichung: 04.09.2012

### <a name="new-features"></a>Neue Funktionen

-   Neue Konfigurationsoption zum Deaktivieren der Verwendung von UnityVS zum Öffnen von Dateien aus Unity.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der Erstellung von Verweisen auf den UnityEditor für Nicht-Editor-Projekte.

-   Korrektur der Definition des UNITY_EDITOR-Symbols für Nicht-Editor-Projekte.

-   Korrektur eines zufälligen VS-Absturzes, der durch unsere benutzerdefinierte Statusleiste verursacht wurde.

## <a name="102"></a>1.0.2
 Veröffentlichung: 30.08.2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur eines Konflikts mit dem PythonTools-Debugger.

-   Korrektur von Verweisen auf Mono.Cecil.

-   Korrektur eines Bugs dahingehend, wie Skriptassemblys mit Unity 4 b7 aus Unity abgerufen werden.

## <a name="101"></a>1.0.1
 Veröffentlichung: 28.08.2012

### <a name="new-features"></a>Neue Funktionen

-   Unterstützung der Vorschau auf Unity 4.0 Beta.

### <a name="bug-fixes"></a>Fehlerkorrekturen

-   Korrektur der Überprüfung der Eigenschaften, die Ausnahmen auslösen.

-   Korrektur beim Wechsel zu Basisobjekten bei der Überprüfung von Objekten.

-   Korrektur einer leeren Dropdownliste für die Einfügemarke im MonoBehavior-Assistenten.

-   Korrektur der Vervollständigung für DLL-Dateien im Ordner "Asset" für UnityScript und Boo.

## <a name="10--initial-release"></a>1.0 – Erstveröffentlichung
 Veröffentlichung: 22.08.2012
