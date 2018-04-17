---
title: 'Vorgehensweise: Migrieren Sie zu Visual Studio 2017 Erweiterungsprojekte | Microsoft Docs'
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93f5d663a31d43dc7a52cbd11261ca78134c682a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Vorgehensweise: Migrieren Sie zu Visual Studio 2017 Erweiterungsprojekte

Dieses Dokument erläutert die Erweiterbarkeit von Projekten auf Visual Studio 2017 aktualisieren. Neben einer Beschreibung, wie Sie die Projektdateien aktualisieren, wird hier beschrieben, auch das upgrade von der Erweiterung manifest v2, Version 2 (VSIX) auf die neue Version 3 VSIX-manifest Format (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installieren Sie Visual Studio 2017 mit erforderlichen arbeitsauslastungen

Stellen Sie sicher, dass die Installation die folgenden Workloads enthält:

* .NET-Desktopentwicklung
* Entwicklung von Visual Studio-Erweiterungen

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Öffnen Sie die VSIX-Projektmappe in Visual Studio 2017

Alle VSIX-Projekte erfordern ein unidirektionales Upgrade der Hauptversion zu Visual Studio 2017.

Die Projektdatei (z. B. csproj-) werden aktualisiert:

* MinimumVisualStudioVersion - 15.0 jetzt festgelegt
* OldToolsVersion (wenn zuvor vorhanden ist)-jetzt auf 14.0 festgelegt.

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualisieren Sie das Microsoft.VSSDK.BuildTools NuGet-Paket

>**Hinweis:** Wenn Ihre Lösung nicht das Microsoft.VSSDK.BuildTools NuGet-Paket verwiesen wird, können Sie diesen Schritt überspringen.

Um Ihre Erweiterung in die neue VSIX v3 erstellen (Version 3)-Format, die Projektmappe wird mit den neuen VSSDK Build-Tools erstellt werden müssen. Dies wird mit Visual Studio 2017 installiert werden, aber die VSIX-v2-Erweiterung kann einen Verweis auf eine frühere Version über NuGet belegen. Wenn dies der Fall ist, müssen Sie ein Update des Microsoft.VSSDK.BuildTools NuGet-Pakets für Ihre Lösung manuell zu installieren.

So aktualisieren Sie die NuGet-Verweise auf Microsoft.VSSDK.BuildTools:

* Mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete für Projektmappe verwalten...**
* Navigieren Sie zu der **Updates** Registerkarte.
* Wählen Sie Microsoft.VSSDK.BuildTools (neueste Version).
* Drücken Sie **Update**.

![VSSDK-Buildtools](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Ändern Sie die VSIX-Erweiterung

Um sicherzustellen, dass der Benutzer die Installation von Visual Studio alle Assemblys, die zum Ausführen der Erweiterung erforderlich ist, geben Sie alle erforderlichen Komponenten oder Pakete in der Manifestdatei für die Erweiterung ein. Wenn ein Benutzer versucht, die Erweiterung zu installieren, wird die VSIXInstaller überprüfen, um festzustellen, ob alle erforderlichen Komponenten installiert sind. Wenn einige fehlen, wird der Benutzer aufgefordert werden, auf die fehlenden Komponenten im Rahmen des Installationsvorgangs Erweiterung zu installieren.

>**Hinweis:** zumindest sollten alle Erweiterungen der Visual Studio Core-Editor-Komponente als erforderliche Komponente angeben.

* Bearbeiten Sie die Erweiterung der Manifestdatei (in der Regel als "Source.Extension.vsixmanifest" bezeichnet).
* Stellen Sie sicher `InstallationTarget` 15.0 enthält.
* Fügen Sie die erforderlichen Installationsvoraussetzungen hinzu (wie im folgenden Beispiel gezeigt).
  * Es wird empfohlen, dass Sie nur über die Komponenten-IDs für die Voraussetzung für die Installation angeben.
  * Finden Sie im Abschnitt am Ende dieses Dokuments für [Anweisungen zum Identifizieren der Komponenten-IDs](#finding-component-ids).

Beispiel:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option: Verwenden des Designers zum Ändern der VSIX-Erweiterung

Anstatt die manifest-XML direkt zu bearbeiten, können Sie die neue **Voraussetzungen** Registerkarte im Manifest-Designer die erforderlichen Komponenten ausgewählt und der XML-Code wird für Sie nicht aktualisiert werden.

>**Hinweis:** Manifest-Designer nur können Sie Komponenten (nicht-Arbeitslasten oder Pakete) auswählen, auf die aktuelle Instanz von Visual Studio installiert sind. Wenn Sie eine Voraussetzung für eine arbeitsauslastung hinzufügen müssen, bearbeiten Paket oder eine Komponente, die derzeit nicht installiert ist, das Manifest-XML direkt.

* Öffnen Sie die Datei "Source.Extension.vsixmanifest" [Entwurf].
* Wählen Sie **Voraussetzungen** Registerkarte, und drücken Sie **neu** Schaltfläche.

  ![VSIX-manifest-designer](media/vsix-manifest-designer.png)

* Die **fügen neue erforderliche** Fenster wird geöffnet.

  ![Fügen Sie die Vsix-Voraussetzung](media/add-vsix-prerequisite.png)

* Klicken Sie auf das Dropdownmenü für **Namen** , und wählen Sie die gewünschte Voraussetzung.
* Aktualisieren Sie die Version aus, falls erforderlich.

  >Hinweis: Das Versionsfeld wird mit der Version der installierten Komponente, mit einem Bereich umfasst bis zu (aber nicht einschließlich) aufgefüllt werden der nächsten Hauptversion von der Komponente.

  ![Roslyn erforderliche Komponente hinzufügen](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>Aktualisieren Sie Debug-Einstellungen für project

Wenn Sie Ihre Erweiterung in einer experimentellen Instanz von Visual Studio debuggen möchten, stellen sicher, dass die projekteinstellungen für **Debuggen** > **Startaktion** hat die **externe starten Programm:** Wert festgelegt wird, auf die Datei "devenv.exe" der 2017 von Visual Studio-Installation.

Es könnte z. B. aussehen:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Externes Programm starten](media/start-external-program.png)

>**Hinweis:** Debuggen Startaktion befindet sich in der Regel in der. csproj.user-Datei. Diese Datei wird in der Regel in der Datei .gitignore enthalten und daher nicht ordnungsgemäß gespeichert mit anderen Projektdateien beim Commit zur quellcodeverwaltung. Als solche, wenn Sie die Projektmappe aus der quellcodeverwaltung frischen abgerufen haben ist es wahrscheinlich das Projekt keine Werte für Startaktion die Option festgelegt hat. Neue VSIX-Projekte mit Visual Studio 2017 erstellt hat eine. csproj.user-Datei mit Standardeinstellungen, die auf das aktuelle Verzeichnis des Visual Studio-Installation erstellt. Wenn Sie eine VSIX-Erweiterung v2 migrieren, es jedoch wahrscheinlich ist, die die. csproj.user-Datei enthält Verweise auf der früheren Version des Visual Studio-Installationsverzeichnis. Festlegen des Werts für **Debuggen** > **Startaktion** lässt die richtige experimentelle Visual Studio-Instanz zu starten, wenn Sie versuchen, Ihre Erweiterung zu debuggen.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Überprüfen Sie, dass die Erweiterung (wie ein VSIX-v3) erstellt

* Erstellen Sie das VSIX-Projekt.
* Entpacken Sie die generierte VSIX.
  * Standardmäßig werden die Arbeit mit VSIX-Datei in "bin" / Debug- oder "bin" / Freigabe als VSIX [YourCustomExtension].
  * Benennen Sie VSIX in .zip, einfach auf den Inhalt anzuzeigen.
* Überprüfen Sie das Vorhandensein von drei Dateien:
  * "Extension.vsixmanifest"
  * Manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Überprüfen Sie, wenn alle erforderliche Komponenten installiert sind

Tests, die VSIX-Pakete auf einem Computer mit der Installation aller erforderlichen Komponenten erfolgreich installiert.

>**Hinweis:** vor dem Installieren einer Erweiterungs, fahren Sie alle Instanzen von Visual Studio.

Versuchen Sie, die Erweiterung zu installieren:

* In Visual Studio 2017

![VSIX-Installationsprogramm für Visual Studio-2017](media/vsixinstaller-vs-2017.png)

* Optional: Überprüfen Sie auf frühere Versionen von Visual Studio.
  * Beweist Abwärtskompatibilität.
  * Sollte für Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 funktionieren.
* Optional: Überprüfen Sie, dass die VSIX-Installationsprogramm Version Checker eine Auswahl von Versionen bietet.
  * Frühere Versionen von Visual Studio umfasst, (falls installiert).
  * Schließt Visual Studio 2017 an.

Wenn Visual Studio zuletzt geöffnet wurde, wird möglicherweise ein Dialogfeld folgendermaßen angezeigt:

![VS laufende Prozesse](media/vs-running-processes.png)

Warten Sie, bis die Prozesse beendet, oder beenden Sie die Aufgaben manuell zu. Sie finden die Prozesse über den aufgeführten Namen oder mit der PID in Klammern aufgeführt.

>**Hinweis:** diese Prozesse werden nicht automatisch heruntergefahren, während eine Instanz von Visual Studio ausgeführt wird. Stellen Sie sicher, dass Sie alle Instanzen von Visual Studio auf dem Computer – einschließlich der von anderen Benutzern heruntergefahren haben, und wiederholen weiterhin.

## <a name="check-when-missing-the-required-prerequisites"></a>Überprüfen Sie, wenn die erforderlichen Komponenten nicht vorhanden.

* Versuchen Sie zum Installieren der Erweiterung auf einem Computer mit Visual Studio 2017, enthält nicht alle Komponenten, die in die erforderlichen Komponenten (oben) definiert.
* Überprüfen Sie, dass die Installation als erforderliche Komponente in der VSIXInstaller listet diese identifiziert die fehlenden Komponente/s an.
* Hinweis: Erhöhung der Rechte ist erforderlich, wenn alle erforderlichen Komponenten mit der Erweiterung installiert werden müssen.

![Vsixinstaller fehlende erforderliche Komponente](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Die Entscheidung für Komponenten

Beim Nachschlagen des Ihre Abhängigkeiten werden Sie feststellen, dass eine Abhängigkeit an mehreren Komponenten zuordnen konnte. Um zu bestimmen, welche Abhängigkeiten, sollten Sie die erforderliche Komponente angeben, es wird empfohlen, dass Sie eine Komponente auswählen, die eine ähnelt der Erweiterung Funktion und, erwägen auch Ihre Benutzer und welche Art von Komponenten würden sie wahrscheinlich installiert haben oder Installieren von ausmacht, wäre nicht. Es wird empfohlen, erstellen, die Ihre Erweiterungen in einer Weise, in denen die erforderlichen Komponenten nur die minimale, die die Erweiterung erfüllen ausgeführt werden kann, und für zusätzliche Funktionen haben sie inaktiv, wenn ein bestimmter Komponenten nicht erkannt werden.

Um weitere Anleitungen bereitzustellen, wurden einige allgemeine Erweiterungstypen und deren Vorkenntnisse ermittelt:

Erweiterungstyp | Anzeigename | Id
--- | --- | ---
Editor | Visual Studio-Kern-Editor  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# und Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Core für Arbeitsauslastung verwalteter Desktops | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Just-In-Time-Debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Suchen nach ComponentIDs

Die Liste der Komponenten, die Visual Studio-Produkten geordnet wird im [Visual Studio 2017 Arbeitslast und die Komponenten-IDs](https://aka.ms/vs2017componentIDs). Verwenden Sie diese Komponenten-IDs für die erforderliche IDs im Manifest an.

Wenn Sie unsicher sind enthält die Komponente einen bestimmten binären Download der [binäres Mapping Spreadsheet-Komponente >](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Es gibt vier Spalten im Excel-Arbeitsblatt: **Komponentenname**, **ComponentId**, **Version**, und **Binary / Dateinamen**.  Sie können die Filter verwenden, um zu suchen, bestimmte Komponenten sowie die Binärdateien.

Für alle Verweise zunächst zu ermitteln, welche die Kernkomponente von-Editor (Microsoft.VisualStudio.Component.CoreEditor) aufweisen.  Mindestens muss die Core-Editor-Komponente als erforderliche Komponente für alle Erweiterungen angegeben werden. Verweise, die überlassen werden, die nicht im Core-Editor sind, fügen Sie Filter in der **Binärdateien / Dateinamen** Abschnitt aus, um Komponenten zu suchen, die die Teilmenge von diesen verweisen.

Beispiele:

* Wenn Sie eine Debuggererweiterung haben und wissen, dass das Projekt einen Verweis auf VSDebugEng.dll und VSDebug.dll verfügt, klicken Sie auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen** Header.  Suchen Sie nach "VSDebugEng.dll", und klicken Sie auf OK.  Klicken Sie anschließend auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen** Header erneut und suchen Sie nach "VSDebug.dll".  Aktivieren Sie das Kontrollkästchen "Aktuelle Auswahl filtern hinzufügen", und wählen Sie OK.  Jetzt Durchsehen der **Komponentenname** eine Komponente zu suchen, die am häufigsten im Zusammenhang mit Ihrem Erweiterungstyp. In diesem Beispiel würden gewählten der Just-In-Time-debugger und die Vsixmanifest hinzugefügt.
* Wenn Sie wissen, dass Ihr Projekt Debugger Elemente behandelt, können Sie suchen, auf "Debugger" in das Suchfeld Filter um festzustellen, welche Komponenten Debugger im Namen enthalten.

## <a name="specifying-a-visual-studio-2017-release"></a>Angeben einer Version von Visual Studio 2017

Wenn die Erweiterung eine bestimmte Version von Visual Studio 2017 erforderlich sind, z. B. Sie davon abhängig ist ein Feature in 15.3 veröffentlicht, müssen Sie die Nummer des Builds in Ihrem VSIX angeben **InstallationTarget**. Version 15.3 hat beispielsweise eine Buildnummer von "15.0.26730.3". Sehen Sie die Zuordnung von Versionen, die zum Erstellen von Zahlen [hier](../install/visual-studio-build-numbers-and-release-dates.md). Verwenden die Versionsnummer "15.3" ist nicht funktionsfähig.

Wenn die Erweiterung 15.3 erfordert oder höher, Sie deklarieren die **InstallationTarget Version** als [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```