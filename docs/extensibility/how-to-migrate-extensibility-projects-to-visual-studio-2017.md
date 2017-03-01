---
title: 'Gewusst wie: Migrieren von Erweiterungsprojekte in Visual Studio 2017 | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 09f14e5b28a506d4f2112f82ee4fd6b0855a8f93
ms.openlocfilehash: 67e143e1b95a0e4d881d7d6bccae0d7445897aa2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Gewusst wie: Migrieren von Erweiterungsprojekte in Visual Studio 2017

>**Hinweis:** diese Dokumentation ist vorläufig und basierend auf der Visual Studio 2017 RC-Version.

Dieses Dokument beschreibt die Erweiterbarkeit Projekte auf Visual Studio 2017 zu aktualisieren. Zusätzlich zu beschreiben, wie die Projektdateien aktualisieren, beschreibt es auch von der Erweiterung manifest v2 Version 2 (VSIX) zum neuen Version 3 VSIX-manifest-Format (VSIX v3) aktualisieren.

## <a name="install-visual-studio-2017-rc-with-required-workloads"></a>Installieren von Visual Studio 2017 RC mit erforderlichen workloads

Stellen Sie sicher, dass die Installation die folgenden Arbeitslasten enthält:

* .NET Desktopentwicklung
* Entwicklung von Visual Studio-Erweiterungen

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Öffnen Sie die VSIX-Projektmappe in Visual Studio 2017

Alle VSIX-Projekte werden ein unidirektionales Upgrade der Hauptversion zu Visual Studio 2017 erfordern.

Die Projektdatei (z. B. *.csproj) werden aktualisiert:

* MinimumVisualStudioVersion - 15.0 jetzt festgelegt
* OldToolsVersion (Wenn bereits vorhanden) – jetzt auf 14.0 festgelegt.

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualisieren Sie das Microsoft.VSSDK.BuildTools NuGet-Paket

>**Hinweis:** , wenn Ihre Lösung nicht das Microsoft.VSSDK.BuildTools NuGet-Paket verwiesen wird, können Sie diesen Schritt überspringen.

Um die Erweiterung in die neue VSIX v3 erstellen (Version 3)-Format, die Projektmappe wird mit den neuen VSSDK Build-Tools erstellt werden müssen. Dies wird mit Visual Studio 2017 RC installiert werden, aber die VSIX-v2-Erweiterung kann einen Verweis auf eine ältere Version über NuGet belegen. Wenn dies der Fall ist, müssen Sie ein Update des Microsoft.VSSDK.BuildTools NuGet-Pakets für die Projektmappe manuell zu installieren. Zum Zeitpunkt der RC-Version wird dieses Paket im Status "Vorabversion" sein.

So aktualisieren Sie die NuGet-Verweise auf Microsoft.VSSDK.BuildTools

* Mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete verwalten...**
* Navigieren Sie zu der **Updates** Registerkarte.
* Aktivieren Sie das Kontrollkästchen **Include Prerelease**.
* Wählen Sie Microsoft.VSSDK.BuildTools (neueste Version).
* Drücken Sie **Update**.

![VSSDK-Buildtools](media/vssdk-build-tools.png)

>**Hinweis:** der Screenshot zeigt eine andere Version von den BuildTools. Wählen Sie die RC-Version.

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Ändern Sie die VSIX-Erweiterung

Um sicherzustellen, dass der Benutzer die Installation von Visual Studio alle Assemblys, die zum Ausführen der Erweiterung erforderlich ist, geben Sie alle erforderlichen Komponenten oder Pakete in der Manifestdatei für die Erweiterung ein. Wenn ein Benutzer versucht, die Erweiterung zu installieren, wird die VSIXInstaller überprüfen, um festzustellen, ob alle erforderlichen Komponenten installiert sind. Wenn einige fehlen, wird der Benutzer aufgefordert werden, um die fehlenden Komponenten im Rahmen der Installation der Erweiterung zu installieren.

* Bearbeiten Sie die Erweiterung der Manifestdatei (in der Regel als "Source.Extension.vsixmanifest" bezeichnet).
* Stellen Sie sicher `InstallationTarget` 15.0 enthält.
* Fügen Sie die erforderlichen Installationsvoraussetzungen hinzu (wie im folgenden Beispiel gezeigt).
  * Es wird empfohlen, dass Sie nur über die Komponenten-IDs für die Installation erforderlichen Komponenten angeben.
  * Finden Sie im Abschnitt am Ende dieses Dokuments [Anweisungen zum Identifizieren von Komponenten-IDs](#finding-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option: Mit dem Designer können Sie die VSIX-Erweiterung ändern

Anstatt das manifest-XML direkt bearbeiten, können Sie die neue **Voraussetzungen** im Manifest-Designer, wählen Sie die erforderlichen Komponenten und die XML-Registerkarte für Sie aktualisiert.

>**Hinweis:** Manifest-Designer nur erlaubt Ihnen, Komponenten (nicht-Arbeitslasten oder Pakete) auswählen, die auf die aktuelle Instanz von Visual Studio installiert sind. Wenn Sie eine Voraussetzung für eine Arbeitslast hinzufügen müssen, bearbeiten Paket oder eine Komponente, die derzeit nicht installiert ist, das Manifest-XML direkt.

* Öffnen Sie die Datei "Source.Extension.vsixmanifest" [Entwurf].
* Wählen Sie **Voraussetzungen** Registerkarte, und drücken Sie **neu** Schaltfläche.

  ![VSIX-manifest-designer](media/vsix-manifest-designer.png)

* Die **Hinzufügen neuer erforderliche** Fenster wird geöffnet.

  ![Fügen Sie die VSIX-Voraussetzung](media/add-vsix-prerequisite.png)

* Klicken Sie auf das Dropdownmenü für **Namen** , und wählen Sie die gewünschten Voraussetzung.
* Aktualisieren Sie die Version aus, falls erforderlich.

  >Hinweis: Das Versionsfeld wird mit der Version der installierten Komponente mit einem Bereich umfasst bis zu (aber nicht einschließlich) aufgefüllt werden die nächste Hauptversion der Komponente.

  ![Roslyn erforderliche Komponente hinzufügen](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>Bei der Migration von Preview 4 oder 5-Vorschau

* Ersetzen Sie `SetupDependencies` mit `Prerequisites` und verschiebt die Elemente, die von der `Installer` Element. `Prerequisites`jetzt sitzt direkt in die `PackageManifest` Element.
* [Optional] Entfernen Sie die `GenerateVsixV3` Element. (Dies wurde in Vorschau 5 nur erforderlich.) Die `GenerateVsixV3` in Versionen als Vorschau 5 Element ignoriert werden.

## <a name="update-debug-settings-for-project"></a>Debugeinstellungen für Projekt aktualisieren

Wenn Sie die Erweiterung in einer experimentellen Instanz von Visual Studio debuggen möchten, stellen sicher, dass die projekteinstellungen für **Debuggen** > **Startaktion** hat die **externes Programm starten:** Wert festgelegt wird, auf die Datei devenv.exe der 2017 für Visual Studio-Installation.

Es sieht aus wie:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Externes Programm starten](media/start-external-program.png)

>**Hinweis:** Debuggen Startaktion befindet sich in der Regel in der. csproj.user-Datei. Diese Datei ist in der Regel in der gitignore-Datei enthalten und daher nicht ordnungsgemäß gespeichert mit anderen Projektdateien, wenn ein Commit in Datenquellen-Steuerelement ausgeführt. Wenn Sie die Projektmappe neue aus Datenquellen-Steuerelement abgerufen haben ist es wahrscheinlich das Projekt keine Werte für Startaktion festgelegt haben. Neue VSIX-Projekte mit Visual Studio 2017 erstellt eine. csproj.user-Datei mit Standardeinstellungen, die auf das aktuelle Verzeichnis des Visual Studio-Installation erstellt. Wenn Sie eine VSIX-v2-Erweiterung migrieren, es jedoch wahrscheinlich ist, die. Datei enthält Verweise auf die vorherigen Visual Studio-Version-Installationsverzeichnis. Festlegen des Werts für **Debuggen** > **Startaktion** ermöglicht die richtige experimentelle Visual Studio-Instanz starten, wenn Sie versuchen, Ihre Erweiterung zu debuggen.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Überprüfen Sie, dass die Erweiterung (wie einem VSIX-v3) erstellt

* Erstellen Sie das VSIX-Projekt.
* Entpacken Sie die generierte VSIX.
  * Standardmäßig werden die VSIX-Datei befindet sich in Bin/Debug oder Bin/Release als VSIX [YourCustomExtension].
  * Benennen Sie VSIX in .zip, einfach den Inhalt anzuzeigen.
* Überprüfen Sie das Vorhandensein von drei Dateien:
  * "Extension.vsixmanifest"
  * "Manifest.JSON"
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Überprüfen Sie, wenn alle erforderliche Komponenten installiert sind

Test, der der VSIX-Datei auf einem Computer mit der Installation aller erforderlichen Komponenten erfolgreich installiert.

>**Hinweis:** vor dem Installieren einer Erweiterungs, fahren Sie alle Instanzen von Visual Studio.

Versuchen Sie, die Erweiterung zu installieren:

* In Visual Studio 2017 RC

![VSIX-Installationsprogramm auf Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Optional: Überprüfen Sie in früheren Versionen von Visual Studio.
  * Stellt Abwärtskompatibilität bereit.
  * Sollte für Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 funktionieren.
* Optional: Überprüfen Sie, ob VSIX-Installationsprogramm Version Checker zwischen Versionen bietet.
  * Frühere Versionen von Visual Studio enthält, (falls installiert).
  * Enthält Visual Studio 2017 RC.

Wenn Visual Studio zuletzt geöffnet wurde, wird möglicherweise ein Dialogfeld wie folgt angezeigt:

![Visual Studio ausgeführte Prozesse](media/vs-running-processes.png)

Warten Sie, bis die Prozesse beendet, oder beenden Sie Aufgaben manuell. Sie finden die Prozesse mit dem angegebenen Namen oder mit der PID in Klammern aufgeführt.

>**Hinweis:** dieser Prozesse werden nicht automatisch geschlossen, während eine Instanz von Visual Studio ausgeführt wird. Stellen Sie sicher, dass Sie alle Instanzen von Visual Studio auf dem Computer, einschließlich von anderen Benutzern heruntergefahren haben und den Vorgang.

## <a name="check-when-missing-the-required-prerequisites"></a>Überprüfen Sie, wenn die erforderlichen Komponenten nicht vorhanden.

* Versuchen Sie zum Installieren der Erweiterung auf einem Computer mit Visual Studio 2017 RC, enthalten nicht alle Komponenten, die in die erforderlichen Komponenten (siehe oben) definiert.
* Überprüfen Sie, dass die Installation die fehlende Komponente/s identifiziert und sie als erforderliche Komponente für die VSIXInstaller zeigt.
* Hinweis: Erhöhte Rechte ist erforderlich, wenn alle erforderlichen Komponenten mit der Erweiterung installiert werden müssen.

![Vsixinstaller Voraussetzung nicht erfüllt.](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Entscheidung für Komponenten

Bei der Suche nach Ihren Abhängigkeiten, finden Sie, dass eine Abhängigkeit an mehreren Komponenten zugeordnet werden. Welche Abhängigkeiten festlegen sollten angeben als die erforderliche Komponente, es wird empfohlen, dass Sie eine Komponente mit einer Funktionalität ist vergleichbar mit der Erweiterung und berücksichtigen auch Benutzer und welche Art von Komponenten würden sie wahrscheinlich installiert haben oder ausmacht, würde nicht installieren. Es wird empfohlen, erstellen, die Ihre Erweiterungen in einer Weise, in denen die erforderlichen Komponenten nur die Mindestanforderungen, die die Erweiterung erfüllen ausgeführt werden kann, und für zusätzliche Features haben sie inaktiv, wenn bestimmte Komponenten nicht erkannt werden.

Um weitere Anleitungen zu gewährleisten, haben wir einige allgemeine Erweiterungstypen und ihre Vorkenntnisse identifiziert:

Erweiterungstyp | Anzeigename |    Id
--- | --- | ---
Editor | Core-Editor von Visual Studio    | Microsoft.VisualStudio.CoreEditor
Roslyn | C# und Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Verwaltete Desktop Arbeitslast Core | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Just-In-Time-debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Suchen nach ComponentIDs

Die Liste der Komponenten, die Visual Studio-Produkt geordnet wird im [Visual Studio 2017 Arbeitslast und Komponenten-IDs](https://aka.ms/vs2017componentIDs). Verwenden Sie diese Komponenten-IDs für die erforderliche IDs im Manifest.

Wenn Sie unsicher sind enthält die Komponente einen bestimmten binären, Download der [-> Zuordnungstabelle binäre Komponente](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Es gibt vier Spalten im Excel-Arbeitsblatt: **Komponentenname**, **ComponentId**, **Version**, und **Binary / Dateinamen**.  Sie können die Filter suchen und finden von Komponenten und Binärdateien.

Für alle Verweise zunächst ermitteln Sie, welche in der Core-Editor (Microsoft.VisualStudio.Component.CoreEditor) sind.  Mindestens benötigen wir die Core-Editor-Komponente als Voraussetzung für alle Erweiterungen angegeben werden. Verweise, die beibehalten werden, die nicht im Kern-Editor, fügen Sie Filter in der **Binärdateien / Dateinamen** Abschnitt, um Komponenten zu suchen, die die Teilmenge der diese Verweise aufweisen.

Beispiele:

* Wenn Sie eine Debuggererweiterung und wissen, dass das Projekt einen Verweis auf VSDebugEng.dll und VSDebug.dll, klicken Sie auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen** Header.  Suchen Sie nach "VSDebugEng.dll", und wählen Sie OK.  Als Nächstes klicken Sie auf die Schaltfläche "Filter" in der **Binärdateien / Dateinamen** Header erneut aus und suchen Sie nach "VSDebug.dll".  Aktivieren Sie das Kontrollkästchen "Aktuelle Auswahl filtern hinzufügen", und wählen Sie OK.  Jetzt Durchsuchen der **Komponentenname** eine Komponente suchen, die am häufigsten im Zusammenhang mit den Erweiterungstyp. In diesem Beispiel würde gewählten Just-In-Time-debugger und die Vsixmanifest hinzugefügt.
* Wenn Sie wissen, dass Ihr Projekt Debugger Elemente behandelt, können Sie suchen, klicken Sie auf "Debugger" in das Suchfeld Filter angezeigt, welche Komponenten Debugger im Namen enthalten.
