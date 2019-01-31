---
title: Optionsseite, Eigenschaften des Knotens „Umgebung“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae1dc5c7eb8b1f10771afacfe1398e17b2bf8ed8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753515"
---
# <a name="options-page-environment-node-properties"></a>Optionsseite, Eigenschaften des Knotens "Umgebung"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
In diesem Dokument werden die Seiten (oder Eigenschaftenauflistungen) beschrieben, die der Kategorie **Umgebung**, `DTE.Properties("Environment", <Property Page>)`, des Dialogfelds **Optionen** zugeordnet sind. Den Titel für jeden Unterabschnitt bildet der Aufruf zum Zugriff auf die Properties-Auflistung, und die Tabelle in jedem Unterabschnitt führt die Eigenschaften in der Auflistung auf.  
  
## <a name="general"></a>Allgemein  
 `DTE.Properties("Environment", "General")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|ShowStatusBar|Get/Set (boolesch)|Bestimmt, ob die Statusleiste sichtbar ist.|  
|WindowMenuContainsNItems|Get/Set (kurzer Name)|Bestimmt, wie Dokumentfenster unten im Windows-Menü erfasst werden.|  
|MRUListContainsNItems|Get/Set (kurzer Name)|Bestimmt, wie viele Dateien im Untermenü "Zuletzt geöffnet" angezeigt werden.|  
|Animationen|Get/Set (boolesch)|Bestimmt, ob die integrierte Entwicklungsumgebung (Integrated Development Environment – IDE) in der Statusleiste Animation verwendet.|  
|AnimationSpeed|Get/Set (kurzer Name)||  
|AutoAdjustExperience|Get/Set (boolesch)|Passt automatisch die visuelle Darstellung entsprechend der Clientleistung an.|  
|RichClientExperienceOptions|Get/Set (Enumeration)|Ermöglicht mit Werten in <xref:EnvDTE100.vsRichClientExperienceOptions> eine umfassende visuelle Darstellung auf dem Client.|  
|CloseButtonActiveTabOnly|Get/Set (boolesch)|Bestimmt, ob die Schaltfläche **Schließen** nur auf der aktiven Registerkarte angezeigt wird.|  
|AutohidePinActiveTabOnly|Get/Set (boolesch)|Bestimmt, ob die Schaltfläche **Automatisch im Hintergrund** nur auf die aktive Registerkarte angewendet wird.|  
  
## <a name="add-inmacros-security"></a>Add-In/Makrosicherheit  
 `DTE.Properties("Environment", "AddinMacrosSecurity")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|MacrosEnabled|Get/Set (boolesch)|Ermöglicht die Ausführung von Makros.|  
|AddinsEnabled|Get/Set (boolesch)|Ermöglicht das Laden von Add-Ins.|  
|LoadAddinsFromTheWeb|Get/Set (boolesch)|Ermöglicht das Laden von Add-Ins über eine URL im Internet.|  
  
## <a name="documents"></a>Dokumente  
 `DTE.Properties("Environment", "Documents")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|ReuseSavedActiveDocWindow|Get/Set (boolesch)|Bestimmt, ob zum Öffnen einer neuen Datei das aktuelle Dokumentfenster verwendet wird, wenn das aktuelle Dokument gespeichert wird. `false` bedeutet, dass für jedes geöffnete Dokument immer ein neues Dokumentfenster verwendet wird.|  
|DetectFileChangesOutsideIDE|Get/Set (boolesch)|Bestimmt, ob die Umgebung in der IDE geöffnete Dateien automatisch neu lädt, wenn das Betriebssystem die IDE benachrichtigt, dass die Dateien auf der Festplatte geändert wurden.|  
|AutoloadExternalChanges|Get/Set (boolesch)|Bestimmt, ob erkannte externe Änderungen an geöffneten Dokumenten zu einem automatischen Neuladen der geänderten Datei führen, wenn am geöffneten Dokument keine Änderungen vorgenommen wurden. Wenn das geöffnete Dokument geändert wurde und diese Eigenschaft auf `true` festgelegt ist, verhält sich die IDE, als ob die Eigenschaft auf `false` festgelegt wäre.|  
|InitializeOpenFileFromCurrentDocument|Get/Set (boolesch)|Bestimmt, ob der Befehl <xref:EnvDTE.DTEClass.OpenFile%2A> auf dem Verzeichnis und Dateinamen des letzten aktiven Dokuments oder auf dem letzten Speicherort basiert, von dem eine Datei geöffnet wurde.|  
|MiscFilesProjectSavesLastNItems|Get/Set (kurzer Name)|Bestimmt die Anzahl der Dateien, die im Projekt Verschiedene Dateien erfasst wird. Das bedeutet, dass beim nächsten Öffnen der IDE angezeigt wird, welche Datei aus dem Projekt Verschiedene Dateien auf der Festplatte geöffnet war.|  
|ShowMiscFilesProject|Get/Set (boolesch)|Bestimmt, ob das Projekt Verschiedene Dateien angezeigt wird.|  
|CheckForConsisentLineEndings|Get/Set (boolesch)|Überprüft beim Laden der Datei Zeilenenden auf Konsistenz.|  
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (boolesch)|Speichert Dokumente als Unicode, wenn Daten nicht in der Codepage gespeichert werden können.|  
|DontShowGlobalUndoChangeLossDialog|Get/Set (boolesch)|Zeigt eine Warnung an, wenn andere bearbeitete Dateien durch globales Rückgängigmachen geändert werden.|  
|AllowEditingReadOnlyFiles|Get/Set (boolesch)|Ermöglicht das Bearbeiten schreibgeschützter Dateien, gibt jedoch eine Warnung aus, wenn versucht wird, die Dateien zu speichern.|  
|DocumentDockPreference|Get/Set (Enumeration)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Die Position in der Gruppe der Registerkarten, an der das geöffnete Dokument eingefügt wird.|  
  
## <a name="extension-manager"></a>Erweiterungs-Manager  
 `DTE.Properties("Environment", "ExtensionManager")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|EnableAdminExtensions|Get/Set (boolesch)|Lädt Erweiterungen pro Benutzer, wenn Visual Studio mit Administratoranmeldeinformationen ausgeführt wird. Visual Studio muss neu gestartet werden, nachdem dieser Wert geändert wurde.|  
|EnableOnline|Get/Set (boolesch)|Ermöglicht den Zugriff auf die Erweiterungen in der Visual Studio Gallery.|  
|AutomaticallyCheckForUpdates|Get/Set (boolesch)|Sucht automatisch nach Updates für installierte Erweiterungen.|  
  
## <a name="find-and-replace"></a>Suchen und Ersetzen  
 `DTE.Properties("Environment", "FindAndReplace")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|ShowWarningMessages|Get/Set (boolesch)|Zeigt Warnmeldungen an.|  
|InitializeFromEditor|Get/Set (boolesch)|Füllt das Feld **Suchen nach** automatisch mit Text aus dem Editor auf.|  
|ShowMessageBoxes|Get/Set (boolesch)|Zeigt Informationsmeldungen an.|  
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (boolesch)|Blendet das Fenster **Suchen und Ersetzen** aus, nachdem mit **Schnellsuche** oder **Schnellersetzung** eine Übereinstimmung gefunden wurde.|  
  
## <a name="import-and-export-settings"></a>Einstellungen importieren und exportieren  
 `DTE.Properties("Environment", "Import and Export Settings")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|TrackTeamSettings|Get/Set (boolesch)|Verwendet die Einstellungen in der von TeamSettingsFile angegebenen Datei.|  
|TeamSettingsFile|Get/Set (Zeichenfolge)|Der Name der Datei, die über Teameinstellungen verfügt.|  
|AutoSaveFile|Get/Set (Zeichenfolge)|Der Name der Datei, in der Benutzereinstellungen automatisch gespeichert werden.|  
  
## <a name="international-settings"></a>Internationale Einstellungen  
 `DTE.Properties("Environment", "International")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|Sprache|Get/Set (Zeichenfolge)|Der LCID-Wert der aktuellen Sprache für Visual Studio.|  
  
## <a name="keyboard"></a>Tastatur  
 `DTE.Properties("Environment", "Keyboard")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|Schema|Get/Set (Zeichenfolge)|Gibt eine Zeichenfolge zurück, die ein integriertes Schema oder den vollständigen Pfad der geladenen VSK-Datei enthält, oder gibt "(Standard)" zurück, wenn keine VSK-Datei geladen ist.|  
  
## <a name="projects-and-solution"></a>Projekte und Projektmappe  
 `DTE.Properties("Environment", "ProjectsAndSolution")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|OnRunOrPreview|Get/Set (Zeichenfolge)|Bestimmt, ob die IDE alles speichert, bevor ein erstelltes Projekt in der Vorschau angezeigt oder ausgeführt wird.|  
|ProjectsLocation|Get/Set (Zeichenfolge)|Bestimmt das Standardverzeichnis, in dem das Dialogfeld **Projekt hinzufügen** neue Projekte speichert.|  
|ShowOutputWindowBeforeBuild|Get/Set (boolesch)|Bestimmt, ob beim Starten eines neuen Buildvorgangs das **Ausgabe**-Fenster angezeigt wird.|  
|ShowTaskListAfterBuild|Get/Set (boolesch)|Bestimmt, ob bei einem fehlgeschlagenen Buildvorgang nach dessen Beendigung die **Aufgabenliste** angezeigt wird.|  
|TrackFileSelectionInExplorer|Get/Set (boolesch)|Bestimmt, ob das aktuelle Element im **Projektmappen-Explorer** verfolgt wird.|  
|AlwaysShowSolutionNode|Get/Set (boolesch)|Bestimmt, ob der Projektmappenknoten angezeigt wird.|  
|OnlySaveStartupProjectsAndDependencies|Get/Set (boolesch)|Bestimmt, ob Speichervorgänge auf Startprojekte und ihre abhängigen Dateien beschränkt werden.|  
|ShowAdvancedBuildConfigurations|Get/Set (boolesch)|Bestimmt, ob erweiterte Buildkonfigurationen angezeigt werden.|  
|ConcurrentBuilds|Get/Set (Zeichenfolge)|Bestimmt die maximale Anzahl von Projektbuilds, die parallel ausgeführt werden können.|  
|SaveNewProjects|Get/Set (boolesch)|Bestimmt, ob neue Projekte nach dem Erstellen automatisch gespeichert werden.|  
|PromptForRenameSymbol|Get/Set (boolesch)|Gibt an, ob beim Umbenennen von Dateien zum symbolischen Umbenennen aufgefordert werden soll.|  
|OnRunWhenErrors|Get/Set (Enumeration)|Gibt das Verhalten bei der Ausführung an, wenn ein Build mit Fehlern abgeschlossen wurde.|  
|OnRunWhenOutOfDate|Get/Set (Enumeration)|Gibt das Verhalten bei der Ausführung an, wenn ein Projekt veraltet ist.|  
|ProjectTemplatesLocation|Get/Set (Zeichenfolge)|Das Verzeichnis, das die Benutzerprojektvorlagen enthält.|  
|ProjectItemTemplatesLocation|Get/Set (Zeichenfolge)|Das Verzeichnis, das die Benutzerelementvorlagen enthält.|  
|DefaultBehaviorForStartupProjects|Get/Set (Zeichenfolge)||  
|MSBuildOutputVerbosity|Get/Set (Zeichenfolge)|Gibt den Ausführlichkeitsgrad für die Buildausgabe an.|  
  
## <a name="startup"></a>Start  
 `DTE.Properties("Environment", "Startup")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|OnStartUp|Get/Set (Enumeration)|Beim Starten auszuführende Aktion aus <xref:EnvDTE.vsStartUp> mit Werten von 0 bis 5:<br /><br /> -   0: Startseite öffnen<br />-   1: Letzte Projektmappe laden<br />-   2: Dialogfeld **Projekt öffnen** anzeigen<br />-   3: Dialogfeld **Neues Projekt** anzeigen<br />-   4: Leere Umgebung anzeigen<br />-   5: Startseite anzeigen|  
|StartPageRSSUrl|Get/Set (Zeichenfolge)|Die URL für den RSS-Feed, der beim Starten verwendet wird.|  
|StartPageRefreshDownloadedContent|Get/Set (boolesch)|Aktualisiert die Startseite nach jedem Ablauf des in StartPageRefreshInterval angegebenen Intervalls.|  
|StartPageRefreshInterval|Get/Set (kurzer Name)|Das Intervall in Minuten, in dem die Startseite aktualisiert wird.|  
  
## <a name="tasklist"></a>TaskList  
 `DTE.Properties("Environment", "TaskList")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|ConfirmTaskDeletion|Get/Set (boolesch)|Gibt an, ob beim Löschen von Aufgaben aus der **Aufgabenliste** ein Bestätigungsdialogfeld angezeigt wird.|  
|WarnOnAddingHiddenItem|Get/Set (boolesch)|Gibt an, ob beim Hinzufügen einer Benutzeraufgabe, die nicht angezeigt wird, eine Warnung angezeigt wird.|  
|DontShowFilePaths|Get/Set (boolesch)|Gibt an, ob in der Aufgabenliste vollständige Dateipfade angezeigt werden.|  
|CommentTokens|SafeArray|Gibt ein SafeArray von Kommentartokenwerten zurück. Es sind jeweils die folgenden Felder enthalten: `Name` (Zeichenfolge) und `Priority` (<xref:EnvDTE.vsTaskPriority>, High, Medium oder Low).|  
  
## <a name="web-browser"></a>Webbrowser  
 `DTE.Properties("Environment", "WebBrowser")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|HomePage|Get/Set (Zeichenfolge)|Stellt die URL der Homepage dar.|  
|SearchPage|Get/Set (Zeichenfolge)|Stellt die URL der Suchseite dar.|  
|ViewSourceIn|Get/Set (Enumeration)|<xref:EnvDTE.vsBrowserViewSource> (Quelle, Entwurf, Extern).|  
|ViewSourceExternalProgram|Get/Set (Zeichenfolge)|Der Pfad für die externe Quellanzeige.|  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Einstellungen im Dialogfeld „Optionen“ (Menü „Extras“)](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Bestimmen der Namen von Eigenschaftenelementen auf Optionsseiten](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Optionsseite, Eigenschaften des Knotens „Schriftarten und Farben“](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Optionsseite, Eigenschaften des Knotens „Text-Editor“](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)
