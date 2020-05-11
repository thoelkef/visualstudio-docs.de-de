---
title: 'Gewusst wie: Migrieren von Erweiterbarkeitsprojekten zu Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710978"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Gewusst wie: Migrieren von Erweiterbarkeitsprojekten zu Visual Studio 2017

In diesem Dokument wird erläutert, wie Erweiterbarkeitsprojekte auf Visual Studio 2017 aktualisiert werden. Neben der Beschreibung der Aktualisierung der Projektdateien wird auch beschrieben, wie von Erweiterungsmanifest Version 2 (VSIX v2) auf das neue VSIX-Manifestformat der Version 3 (VSIX v3) aktualisiert wird.

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installieren von Visual Studio 2017 mit erforderlichen Workloads

Stellen Sie sicher, dass Ihre Installation die folgenden Workloads umfasst:

* .NET-Desktopentwicklung
* Entwicklung von Visual Studio-Erweiterungen

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Öffnen der VSIX-Lösung in Visual Studio 2017

Für alle VSIX-Projekte ist ein einmaliges Upgrade auf Visual Studio 2017 erforderlich.

Die Projektdatei (z. B. **.csproj*) wird aktualisiert:

* MinimumVisualStudioVersion - jetzt auf 15.0 gesetzt
* OldToolsVersion (falls vorhanden) - jetzt auf 14.0 gesetzt

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aktualisieren des Microsoft.VSSDK.BuildTools NuGet-Pakets

> [!Note]
> Wenn Ihre Lösung nicht auf das Microsoft.VSSDK.BuildTools NuGet-Paket verweist, können Sie diesen Schritt überspringen.

Um Ihre Erweiterung im neuen VSIX v3-Format (Version 3) zu erstellen, muss Ihre Lösung mit den neuen VSSDK Build Tools erstellt werden. Dies wird mit Visual Studio 2017 installiert, aber Ihre VSIX v2-Erweiterung kann einen Verweis auf eine ältere Version über NuGet enthalten. Wenn dies der Fall ist, müssen Sie manuell ein Update des Microsoft.VSSDK.BuildTools NuGet-Pakets für Ihre Lösung installieren.

So aktualisieren Sie die NuGet-Referenzen auf Microsoft.VSSDK.BuildTools:

* Klicken Sie mit der rechten Maustaste auf die Lösung und wählen **Sie NuGet-Pakete für Die Lösung verwalten**.
* Navigieren Sie zur Registerkarte **Updates.**
* Wählen Sie **Microsoft.VSSDK.BuildTools (neueste Version)** aus.
* Drücken Sie **Update**.

![VSSDK-Buildtools](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Änderungen am VSIX-Erweiterungsmanifest vornehmen

Um sicherzustellen, dass die Installation von Visual Studio durch den Benutzer über alle Assemblys verfügt, die zum Ausführen der Erweiterung erforderlich sind, geben Sie alle erforderlichen Komponenten oder Pakete in der Erweiterungsmanifestdatei an. Wenn ein Benutzer versucht, die Erweiterung zu installieren, überprüft der VSIXInstaller, ob alle Voraussetzungen installiert sind. Wenn einige fehlen, wird der Benutzer aufgefordert, die fehlenden Komponenten als Teil des Erweiterungsinstallationsprozesses zu installieren.

> [!Note]
> Mindestens sollten alle Erweiterungen die Visual Studio-Kerneditorkomponente als Voraussetzung angeben.

* Bearbeiten Sie die Erweiterungsmanifestdatei (in der Regel *source.extension.vsixmanifest*genannt).
* Stellen `InstallationTarget` Sie sicher, enthält 15.0.
* Fügen Sie erforderliche Installationsvoraussetzungen hinzu (wie im folgenden Beispiel gezeigt).
  * Es wird empfohlen, nur Komponenten-IDs für Installationsvoraussetzungen anzugeben.
  * Anweisungen zum Identifizieren von [Komponenten-IDs](#find-component-ids)finden Sie im Abschnitt am Ende dieses Dokuments .

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option: Verwenden Sie den Designer, um Änderungen am VSIX-Erweiterungsmanifest vorzunehmen

Anstatt das Manifest XML direkt zu bearbeiten, können Sie die neue Registerkarte **Voraussetzungen** im Manifest-Designer verwenden, um die Voraussetzungen auszuwählen, und der XML-Code wird für Sie aktualisiert.

> [!Note]
> Mit dem Manifest-Designer können Sie nur Komponenten (nicht Workloads oder Pakete) auswählen, die auf der aktuellen Visual Studio-Instanz installiert sind. Wenn Sie eine Voraussetzung für eine Workload, ein Paket oder eine Komponente hinzufügen müssen, die derzeit nicht installiert ist, bearbeiten Sie das Manifest XML direkt.

* Open *source.extension.vsixmanifest [Design]* Datei.
* Wählen Sie die Registerkarte **Voraussetzungen** aus, und drücken Sie die Taste **Neu.**

   ![VSIX-Manifestdesigner](media/vsix-manifest-designer.png)

* Das Fenster **Neue Voraussetzung hinzufügen** wird geöffnet.

   ![Hinzufügen von vsix-Voraussetzung](media/add-vsix-prerequisite.png)

* Klicken Sie auf die Dropdown-Liste für **Name** und wählen Sie die gewünschte Voraussetzung aus.
* Aktualisieren Sie die Version bei Bedarf.

   > [!Note]
   > Das Versionsfeld wird mit der Version der aktuell installierten Komponente vorab ausgefüllt, wobei ein Bereich bis zur nächsten Hauptversion der Komponente reicht (aber nicht einspannen).

   ![Roslyn-Voraussetzung hinzufügen](media/add-roslyn-prerequisite.png)

* Klicken Sie auf **OK**.

## <a name="update-debug-settings-for-the-project"></a>Debug-Einstellungen für das Projekt aktualisieren

Wenn Sie Ihre Erweiterung in einer experimentellen Instanz von Visual Studio debuggen möchten, stellen Sie sicher, dass die Projekteinstellungen für die **Aktion Debugstart** > **Start action** den **externen Startprogramm:** Wert auf die Datei *devenv.exe* Ihrer Visual Studio 2017-Installation festgelegt haben.

Es könnte wie folgt aussehen: *C:-Programmdateien (x86)*

![Externes Programm starten](media/start-external-program.png)

> [!Note]
> Die Debugstartaktion wird in der Regel in der *Datei .csproj.user* gespeichert. Diese Datei ist in der Regel in der *.gitignore-Datei* enthalten und wird daher normalerweise nicht mit anderen Projektdateien gespeichert, wenn sie an die Quellcodeverwaltung gebunden ist. Wenn Sie die Projektmappe aus der Quellcodeverwaltung neu gezogen haben, ist es wahrscheinlich, dass für das Projekt keine Werte für Startaktion festgelegt sind. Bei neuen VSIX-Projekten, die mit Visual Studio 2017 erstellt wurden, wird eine *.csproj.user-Datei* erstellt, deren Standardeinstellungen auf das aktuelle Visual Studio-Installationsverzeichnis verweisen. Wenn Sie jedoch eine VSIX v2-Erweiterung migrieren, ist es wahrscheinlich, dass die *.csproj.user-Datei* Verweise auf das Installationsverzeichnis der vorherigen Visual Studio-Version enthält. Wenn Sie den Wert für die **Aktion Debugstart** > **festlegen,** kann die richtige experimentelle Visual Studio-Instanz gestartet werden, wenn Sie versuchen, die Erweiterung zu debuggen.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Überprüfen Sie, ob die Erweiterung korrekt erstellt wird (als VSIX v3)

* Erstellen Sie das VSIX-Projekt.
* Entpacken Sie den generierten VSIX.
  * Standardmäßig befindet sich die VSIX-Datei innerhalb *von bin/Debug* oder *bin/Release* als *[YourCustomExtension].vsix*.
  * Benennen Sie *.vsix* in *.zip* um, um den Inhalt einfach anzuzeigen.
* Überprüfen Sie, ob drei Dateien vorhanden sind:
  * *Extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Überprüfen Sie, ob alle erforderlichen Voraussetzungen installiert sind

Testen Sie, ob der VSIX erfolgreich auf einem Computer installiert wird, auf dem alle erforderlichen Voraussetzungen installiert sind.

> [!Note]
> Fahren Sie vor der Installation einer Erweiterung alle Instanzen von Visual Studio herunter.

Versuchen Sie, die Erweiterung zu installieren:

* Auf Visual Studio 2017

![VSIX-Installationsprogramm auf Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Optional: Überprüfen Sie frühere Versionen von Visual Studio.
  * Beweist Abwärtskompatibilität.
  * Sollte für Visual Studio 2012, Visual Studio 2013, Visual Studio 2015 arbeiten.
* Optional: Überprüfen Sie, ob VSIX Installer Version Checker eine Auswahl an Versionen bietet.
  * Enthält frühere Versionen von Visual Studio (falls installiert).
  * Enthält Visual Studio 2017.

Wenn Visual Studio kürzlich geöffnet wurde, wird möglicherweise ein Dialogfeld wie folgt angezeigt:

![im Vergleich zu laufenden Prozessen](media/vs-running-processes.png)

Warten Sie, bis die Prozesse heruntergefahren sind, oder beenden Sie die Vorgänge manuell. Sie können die Prozesse anhand des aufgeführten Namens oder mit der in Klammern aufgeführten PID finden.

> [!Note]
> Diese Prozesse werden nicht automatisch heruntergefahren, während eine Instanz von Visual Studio ausgeführt wird. Stellen Sie sicher, dass Sie alle Instanzen von Visual Studio auf dem Computer heruntergefahren haben – einschließlich der Instanzen anderer Benutzer , und wiederholen Sie den Vorgang.

## <a name="check-when-missing-the-required-prerequisites"></a>Überprüfen Sie, ob die erforderlichen Voraussetzungen fehlen

* Versuchen Sie, die Erweiterung auf einem Computer mit Visual Studio 2017 zu installieren, der NICHT alle in den Voraussetzungen definierten Komponenten (oben) ENTHÄLT.
* Überprüfen Sie, ob die Installation die fehlenden Komponenten identifiziert und sie als Voraussetzung im VSIXInstaller auflistet.
* Hinweis: Eine Erhöhung ist erforderlich, wenn die Voraussetzungen für die Erweiterung erforderlich sind.

![vsixinstaller fehlt Voraussetzung](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Entscheiden Sie über Komponenten

Wenn Sie Ihre Abhängigkeiten nachsehen, werden Sie feststellen, dass eine Abhängigkeit mehreren Komponenten zugeordnet werden kann. Um zu bestimmen, welche Abhängigkeiten Sie als Voraussetzung angeben sollten, empfehlen wir Ihnen, eine Komponente auszuwählen, die eine Ähnliche Funktionalität wie Ihre Erweiterung hat, und auch Ihre Benutzer zu berücksichtigen und zu berücksichtigen, welche Art von Komponenten sie höchstwahrscheinlich installiert haben oder nichts dagegen hätten, zu installieren. Wir empfehlen auch, Ihre Erweiterungen so zu erstellen, dass die erforderlichen Voraussetzungen nur das Minimum erfüllen, das die Ausführung Ihrer Erweiterung ermöglicht, und für zusätzliche Funktionen ruhen sie, wenn bestimmte Komponenten nicht erkannt werden.

Um weitere Hinweise zu geben, haben wir einige gemeinsame Erweiterungstypen und deren vorgeschlagene Voraussetzungen identifiziert:

Erweiterungstyp | Anzeigename | id
--- | --- | ---
Editor | Visual Studio-Kern-Editor | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# und Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Core für Arbeitsauslastung verwalteter Desktops | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Just-In-Time-Debugger | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Suchen von Komponenten-IDs

Die Liste der nach Visual Studio-Produkt sortierten Komponenten finden Sie unter [Visual Studio 2017 Workload und Komponenten-IDs](/visualstudio/install/workload-and-component-ids?view=vs-2019). Verwenden Sie diese Komponenten-IDs für Ihre erforderlichen IDs in Ihrem Manifest.

Wenn Sie sich nicht sicher sind, welche Komponente eine bestimmte Binärdatei enthält, laden Sie die [Tabelle "Component -> Binary Mapping" herunter.](https://aka.ms/vs2017componentid-binaries)

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Es gibt vier Spalten im Excel-Blatt: **Komponentenname**, **ComponentId**, **Version**und **Binär - Dateinamen**.  Sie können die Filter verwenden, um bestimmte Komponenten und Binärdateien zu suchen und zu suchen.

Bestimmen Sie für alle Referenzen zunächst, welche im Kerneditor (Microsoft.VisualStudio.Component.CoreEditor) enthalten sind.  Wir müssen mindestens die Kerneditorkomponente als Voraussetzung für alle Erweiterungen angegeben haben. Von den Linksverweisen, die sich nicht im Kerneditor befinden, fügen Sie Filter im Abschnitt **Binärdateien / Dateinamen** hinzu, um Komponenten zu finden, die eine der Teilmengen dieser Verweise enthalten.

Beispiele:

* Wenn Sie über eine Debuggererweiterung verfügen und wissen, dass Ihr Projekt einen Verweis auf *VSDebugEng.dll* und *VSDebug.dll*enthält, klicken Sie auf die Filterschaltfläche im Header **Binaries / Files Names.**  Suchen Sie nach "VSDebugEng.dll" und wählen Sie *OK*.  Klicken Sie dann erneut auf die Filterschaltfläche im **Kopfzeile Binaries / Files Names** und suchen Sie nach "VSDebug.dll".  Aktivieren Sie das Kontrollkästchen **Aktuelle Auswahl hinzufügen, um zu filtern,** und wählen Sie **OK**aus.  Suchen Sie nun im **Komponentennamen** nach einer Komponente, die sich am meisten auf Ihren Erweiterungstyp bezieht. In diesem Beispiel wählen Sie den Just-In-Time-Debugger aus und fügen ihn Ihrem vsixmanifest hinzu.
* Wenn Sie wissen, dass sich Ihr Projekt mit Debuggerelementen befasst, können Sie im Filtersuchfeld nach "Debugger" suchen, um zu sehen, welche Komponenten den Debugger im Namen enthalten.

## <a name="specify-a-visual-studio-2017-release"></a>Angeben einer Visual Studio 2017-Version

Wenn Ihre Erweiterung z. B. eine bestimmte Version von Visual Studio 2017 erfordert, hängt dies von einem feature ab, das in 15.3 veröffentlicht wurde, und Sie müssen die Buildnummer in Ihrem VSIX **InstallationTarget**angeben. Version 15.3 hat beispielsweise die Buildnummer '15.0.26730.3'. Sie können die Zuordnung von Releases zum Erstellen von Nummern [hier](../install/visual-studio-build-numbers-and-release-dates.md)sehen. Die Verwendung der Versionsnummer '15.3' funktioniert nicht korrekt.

Wenn Ihre Erweiterung 15.3 oder höher erfordert, würden Sie die **InstallationTarget-Version** als [15.0.26730.3, 16.0) deklarieren:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
