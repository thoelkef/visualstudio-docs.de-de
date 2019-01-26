---
title: 'Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017 | Microsoft-Dokumentation'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3726ee6995e770d89e5916a922c0546439c3ba14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953509"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017

Dieses Dokument erläutert das upgrade von Erweiterungsprojekten zu Visual Studio 2017. Zusätzlich zu beschreiben, wie Sie die Projektdateien zu aktualisieren, beschreibt es auch von der Erweiterung manifest der Version 2 (v2 VSIX) auf die neue Version 3 VSIX-Manifestformat (VSIX v3) aktualisieren.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installieren von Visual Studio 2017 mit erforderlichen arbeitsauslastungen

Stellen Sie sicher, dass die Installation die folgenden Workloads enthält:

* .NET-Desktopentwicklung
* Entwicklung von Visual Studio-Erweiterungen

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Öffnen Sie die VSIX-Projektmappe in Visual Studio 2017

Alle VSIX-Projekte müssen ein unidirektionales Upgrade der Hauptversion zu Visual Studio 2017.

Die Projektdatei (z. B. **csproj*) aktualisiert werden:

* MinimumVisualStudioVersion - now set to 15.0
* OldToolsVersion (wenn zuvor vorhanden ist) – jetzt auf 14.0 festgelegt.

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualisieren von NuGet-Paket Microsoft.VSSDK.BuildTools

>**Hinweis**: Wenn Ihre Lösung nicht über die NuGet-Paket Microsoft.VSSDK.BuildTools verweist, können Sie diesen Schritt überspringen.

Um die Erweiterung in die neue VSIX v3 zu erstellen (Version 3)-Format, Ihre Lösung mit den neuen VSSDK-Build-Tools erstellt werden müssen. Dies wird mit Visual Studio 2017 installiert, aber Ihre VSIX-v2-Erweiterung kann einen Verweis auf eine ältere Version über NuGet belegen. Wenn dies der Fall ist, müssen Sie ein Update des NuGet-Paket Microsoft.VSSDK.BuildTools für Ihre Lösung manuell zu installieren.

So aktualisieren Sie die NuGet-Verweise auf Microsoft.VSSDK.BuildTools:

* Mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete für Projektmappe verwalten**.
* Navigieren Sie zu der **Updates** Registerkarte.
* Wählen Sie **Microsoft.VSSDK.BuildTools (neueste Version)**.
* Drücken Sie **Update**.

![VSSDK-Buildtools](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Nehmen Sie Änderungen an der VSIX-erweiterungsmanifests.

Um sicherzustellen, dass der Benutzer die Installation von Visual Studio alle Assemblys, die zum Ausführen der Erweiterung erforderlich ist, geben Sie alle erforderlichen Komponenten oder Pakete in der Manifestdatei für die Erweiterung ein. Wenn ein Benutzer versucht, die die Erweiterung zu installieren, überprüft der VSIX-Installationsprogramm, um festzustellen, ob alle erforderlichen Komponenten installiert sind. Wenn einige fehlen, wird der Benutzer aufgefordert werden, um die fehlenden Komponenten im Rahmen des Installationsvorgangs Erweiterung zu installieren.

>**Hinweis**: Zumindest sollten alle Erweiterungen der Visual Studio-Kern-Editor-Komponente als erforderliche Komponente angeben.

* Bearbeiten Sie die Erweiterung manifest-Datei (in der Regel aufgerufen *"Source.Extension.vsixmanifest"*).
* Stellen Sie sicher `InstallationTarget` 15.0 umfasst.
* Fügen Sie die erforderlichen Installationsvoraussetzungen hinzu (wie im folgenden Beispiel gezeigt).
  * Es wird empfohlen, dass Sie die Voraussetzungen für die Installation nur Komponenten-IDs angeben.
  * Finden Sie im Abschnitt am Ende dieses Dokuments auch für [Anweisungen zum Identifizieren der Komponenten-IDs](#find-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option: Verwenden Sie den Designer, um die VSIX-erweiterungsmanifests zu ändern

Anstatt das manifest-XML direkt zu bearbeiten, können Sie die neue **Voraussetzungen** Registerkarte im Manifest-Designer, wählen Sie die Voraussetzungen und den XML-Code für Sie aktualisiert werden.

>**Hinweis**: Der Manifest-Designer lässt nur das Auswählen von Komponenten (nicht "Workloads" oder "Pakete"), die in der aktuellen Visual Studio-Instanz installiert sind. Wenn Sie eine Voraussetzung für eine Workload hinzufügen müssen, bearbeiten Paket oder einer Komponente, die derzeit nicht installiert ist, das Manifest-XML direkt.

* Open *"Source.Extension.vsixmanifest" [Entwurf]* Datei.
* Wählen Sie **Voraussetzungen** Registerkarte, und drücken Sie **neu** Schaltfläche.

  ![VSIX-manifest-designer](media/vsix-manifest-designer.png)

* Die **neue Voraussetzung hinzufügen** Fenster wird geöffnet.

  ![Fügen Sie die VSIX-Voraussetzungen](media/add-vsix-prerequisite.png)

* Klicken Sie auf das Dropdownmenü für **Namen** , und wählen Sie die gewünschte Voraussetzung.
* Aktualisieren Sie die Version aus, falls erforderlich.

  >Hinweis: Das Versionsfeld werden vorab ausgefüllt, mit der Version der derzeit installierten Komponente mit einem Bereich umfasst bis zu (aber nicht einschließlich) der nächsten Hauptversion von der Komponente.

  ![Hinzufügen der Roslyn-Voraussetzungen](media/add-roslyn-prerequisite.png)

* Klicken Sie auf **OK**.

## <a name="update-debug-settings-for-the-project"></a>Debug-Einstellungen für das Projekt aktualisieren

Wenn Sie Ihre Erweiterung in einer experimentellen Instanz von Visual Studio debuggen möchten, stellen sicher, dass die projekteinstellungen für **Debuggen** > **Startaktion** hat die **externe starten Programm:** Wert festgelegt wird, um die *devenv.exe* Datei der Visual Studio 2017-Installation.

Dies kann so aus: *C:\Programme\Microsoft Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Externes Programm starten](media/start-external-program.png)

>**Hinweis**: Debuggen von Startaktion befindet sich in der Regel in der *. csproj.user* Datei. Diese Datei befindet sich in der Regel in der *".gitignore"* Datei, und daher nicht Normal gespeichert mit anderen Projektdateien, wenn ein Commit in die quellcodeverwaltung ausgeführt. Wenn Sie die Projektmappe aus der quellcodeverwaltung neue abgerufen haben ist es wahrscheinlich das Projekt keine Werte für Startaktion festgelegt hat. Neue VSIX-Projekte mit Visual Studio 2017 erstellt haben eine *. csproj.user* Datei erstellt, die mit den Standardeinstellungen für das aktuelle Visual Studio-Installationsverzeichnis verweist. Wenn Sie eine VSIX-Erweiterung v2 migrieren, es jedoch wahrscheinlich ist, die die *. csproj.user* -Datei enthält Verweise auf der früheren Version des Visual Studio-Installationsverzeichnis. Festlegen des Werts für **Debuggen** > **Startaktion** ermöglicht die richtige experimentelle Visual Studio-Instanz zum Starten, wenn Sie versuchen, Ihre Erweiterung zu debuggen.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Überprüfen Sie, dass die Erweiterung (wie eine VSIX v3) erstellt.

* Erstellen Sie das VSIX-Projekt.
* Entzippen Sie die generierte VSIX-Datei aus.
  * Standardmäßig befindet sich die VSIX-Datei in *Bin/Debug* oder *Bin/Release* als *[YourCustomExtension] VSIX*.
  * Benennen Sie *VSIX* zu *ZIP* , einfach den Inhalt anzuzeigen.
* Überprüfen Sie das Vorhandensein von drei Dateien:
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Überprüfen Sie, wenn alle erforderliche Komponenten installiert sind

Test, der die VSIX-Datei auf einem Computer mit allen erforderlichen Komponenten installiert wurde erfolgreich installiert.

>**Hinweis**: Vor der Installation alle Erweiterungen, beenden Sie alle Instanzen von Visual Studio.

Versucht, die die Erweiterung zu installieren:

* Für Visual Studio 2017

![VSIX-Installer für Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Optional: Überprüfen Sie in früheren Versionen von Visual Studio.
  * Stellt die Abwärtskompatibilität zu gewährleisten.
  * Sollte funktionieren für Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Optional: Überprüfen Sie, dass die VSIX-Installer-Version aus eine Auswahl von Versionen bietet.
  * Enthält frühere Versionen von Visual Studio (falls installiert).
  * Enthält Visual Studio 2017.

Wenn Visual Studio zuletzt geöffnet wurde, wird möglicherweise ein Dialogfeld wie folgt angezeigt:

![Visual Studio ausgeführte Prozesse](media/vs-running-processes.png)

Warten Sie, bis die Prozesse beendet, oder beenden Sie die Tasks manuell. Sie finden die Prozesse durch den aufgeführten Namen oder mit der PID, die in Klammern aufgeführt.

>**Hinweis**: Diese Prozesse werden nicht automatisch heruntergefahren, während eine Instanz von Visual Studio ausgeführt wird. Stellen Sie sicher, dass Sie alle Instanzen von Visual Studio auf dem Computer – einschließlich der von anderen Benutzern oder beendet haben, dann zu wiederholen.

## <a name="check-when-missing-the-required-prerequisites"></a>Überprüfen Sie, wenn die erforderlichen Komponenten fehlt.

* Versuchen Sie zum Installieren der Erweiterung auf einem Computer mit Visual Studio 2017, enthalten nicht alle Komponenten, die im Rahmen der Vorbereitung (oben) definiert.
* Überprüfen Sie, dass die Installation die fehlende Komponente/s identifiziert und sie als erforderliche Komponente für das VSIX-Installationsprogramm listet an.
* Hinweis: Erhöhung der Rechte ist erforderlich, wenn alle erforderlichen Komponenten mit der Erweiterung installiert werden müssen.

![VSIX-Installationsprogramm fehlende erforderliche Komponente](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Entscheiden Sie sich für Komponenten

Beim Nachschlagen von Abhängigkeiten, werden Sie feststellen, dass eine Abhängigkeit für mehrere Komponenten zuordnen konnte. Um zu bestimmen, welche Abhängigkeiten Sie angeben, wie Ihre Voraussetzung ist sollten, es wird empfohlen, dass Sie eine Komponente auswählen, die zu Ihrer Erweiterung vergleichbare Funktion, und, berücksichtigen auch Ihre Benutzer und welche Art von Komponenten würden sie in den meisten Fällen installiert haben oder wäre nicht installieren sollten. Es wird empfohlen, erstellen, die Ihre Erweiterungen in einer Weise, in denen die erforderlichen Komponenten nur das Minimum erfüllen können, das die Erweiterung ausgeführt werden kann, und für zusätzliche Features lassen werden inaktiv, wenn sicher, dass Komponenten nicht erkannt werden.

Um weitere Hilfestellung zu bieten, haben wir einige allgemeine Erweiterungstypen und ihre Vorkenntnisse identifiziert:

Erweiterungstyp | Anzeigename | Id
--- | --- | ---
Editor | Visual Studio-Kern-Editor  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# und Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Core für Arbeitsauslastung verwalteter Desktops | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Just-In-Time-Debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Suchen Sie die Komponenten-IDs

Die Liste der Komponenten, sortiert nach Visual Studio-Produkt ist unter [arbeitsauslastungs- und Komponenten-IDs von Visual Studio 2017](https://aka.ms/vs2017componentIDs). Verwenden Sie diese Komponenten-IDs für Ihren erforderlichen Komponenten-IDs im Manifest an.

Wenn Sie nicht sicher sind, welche Komponente eine bestimmte Binärdatei enthält, laden Sie die [binäres Mapping-Arbeitsblatt-Komponente >](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>Visual Studio 2017-ComponentBinaryMapping.xlsx

Es gibt vier Spalten im Excel-Arbeitsblatt ein: **Name der Komponente**, **ComponentId**, **Version**, und **Binary / Dateinamen**.  Sie können die Filter verwenden, die Suche nach bestimmten Komponenten und -Binärdateien.

Für alle Ihre Verweise zunächst bestimmen Sie, welche in der Kern-Editor (Microsoft.VisualStudio.Component.CoreEditor) Komponente sind.  Zumindest müssen die Kern-Editor-Komponente als Voraussetzung für alle Erweiterungen angegeben werden. Verweise, die beibehalten werden, deren nicht-Kern-Editor, fügen Sie Filter in der **Binärdateien / Dateinamen** Abschnitt aus, um Komponenten zu suchen, die die Teilmenge der diese Verweise aufweisen.

Beispiele:

* Wenn Sie eine Debuggererweiterung und wissen, dass Ihr Projekt einen Verweis auf *VSDebugEng.dll* und *VSDebug.dll*, klicken Sie auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen**Header.  Suchen Sie nach "VSDebugEng.dll", und wählen Sie *OK*.  Klicken Sie dann auf, auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen** Header erneut aus und suchen Sie nach "VSDebug.dll".  Aktivieren Sie das Kontrollkästchen **fügen Sie die aktuelle Auswahl dem filter** , und wählen Sie **OK**.  Durchsuchen Sie jetzt die **Komponentenname** eine Komponente suchen, die am meisten im Zusammenhang mit der Ihr Erweiterungstyp. In diesem Beispiel würde gewählten die Just-In-Time-debugger und Ihre Vsixmanifest hinzuzufügen.
* Wenn Sie wissen, dass Ihr Projekt mit dem Debugger-Elemente behandelt, können Sie suchen, klicken Sie auf "Debuggen" in das filtersuchfeld um festzustellen, welche Komponenten Debugger im Namen enthalten.

## <a name="specify-a-visual-studio-2017-release"></a>Geben Sie ein Visual Studio 2017-release

Wenn die Erweiterung eine bestimmte Version von Visual Studio 2017 erforderlich sind, z. B. ein Feature in Version 15.3 hängt, müssen Sie die Nummer des Builds in VSIX Einbeziehen angeben **"installationtarget"**. Beispielsweise hat in Version 15.3 eine Buildnummer von "15.0.26730.3". Sehen Sie die Zuordnung von Releases fest, erstellen Sie Zahlen [hier](../install/visual-studio-build-numbers-and-release-dates.md). Verwenden die Versionsnummer "15.3" ist nicht funktionsfähig.

Wenn Ihre Erweiterung erforderlich, Version 15.3 ist oder höher verwenden, müssten Sie deklarieren die **"installationtarget" Version** als [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
