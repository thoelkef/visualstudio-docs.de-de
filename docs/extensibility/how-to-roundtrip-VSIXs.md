---
title: Wie Sie die Roundtrip-Erweiterungen
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 07a9363eef7d350ddbc7ec55f9fab62f38dadc1d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710603"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Vorgehensweise: Machen Sie Erweiterungen kompatibel mit Visual Studio 2017 und Visual Studio 2015

Dieses Dokument erläutert, wie Sie Erweiterungsprojekte Roundtrip zwischen Visual Studio 2015 und Visual Studio 2017. Nach Abschluss dieser Aktualisierung werden ein Projekt öffnen, erstellen, installieren, und führen Sie in Visual Studio 2015 und Visual Studio 2017. Als Referenz, einige Erweiterungen, die einen Roundtrip zwischen Visual Studio 2015 und Visual Studio 2017 finden Sie in der [VS-SDK-Erweiterbarkeitsbeispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Wenn Sie nur in Visual Studio 2017 erstellen, sondern soll die Ausgabe von VSIX in Visual Studio 2015 und Visual Studio 2017 ausführen möchten, verweisen Sie dann auf die [Erweiterung dokumentu migrace](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Aufgrund von Änderungen in Visual Studio zwischen den Versionen funktionieren nicht einige Dinge, die in einer bestimmten Version funktioniert in einer anderen. Stellen Sie sicher, dass die Funktionen, die Sie zugreifen möchten, in beiden Versionen verfügbar sind oder die Erweiterung hat unerwartete Ergebnisse.

Hier ist eine Übersicht über die Schritte, die Sie in diesem Dokument eine VSIX-Roundtrip abgeschlossen werden:

1. Importieren Sie die richtige NuGet-Pakete.
2. Aktualisieren Sie die Erweiterungsmanifest:
    * Installationsziel
    * Vorraussetzungen
3. Aktualisieren Sie die CSProj:
    * Update `<MinimumVisualStudioVersion>`.
    * Hinzufügen der `<VsixType>` Eigenschaft.
    * Fügen Sie die Debug-Eigenschaft `($DevEnvDir)` 3 Mal.
    * Fügen Sie Bedingungen für das Importieren von Build-Tools und -Ziele.

4. Erstellen und testen

## <a name="environment-setup"></a>Einrichten der Umgebung

In diesem Dokument wird davon ausgegangen, dass Sie Folgendes auf Ihrem Computer installiert haben:

* Visual Studio 2015 mit dem Visual Studio SDK
* Visual Studio 2017 mit installierter Workload für die Erweiterbarkeit

## <a name="recommended-approach"></a>Empfohlene Vorgehensweise

Es wird dringend empfohlen, um das Upgrade mit Visual Studio 2015, anstelle von Visual Studio 2017 zu starten. Der Hauptvorteil der Entwicklung in Visual Studio 2015 wird sichergestellt, dass Sie nicht auf Assemblys verweisen, die nicht in Visual Studio 2015 verfügbar sind. Wenn Sie die Entwicklung in Visual Studio 2017 tun, besteht die Gefahr, die Sie mit eine Abhängigkeit zu einer Assembly erfolgen, die nur in Visual Studio 2017 vorhanden ist.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Stellen Sie sicher, dass es ist kein Verweis auf Datei "Project.JSON"

Weiter unten in diesem Dokument werden wir fügen Sie bedingte Import-Anweisungen in Ihre **csproj* Datei.  Dies funktioniert nicht, wenn die NuGet-Verweise in gespeichert sind *"Project.JSON"*. Es wird daher empfohlen, verschieben Sie alle NuGet-Verweise auf die *"Packages.config"* Datei.
Wenn das Projekt enthält eine *"Project.JSON"* Datei:

* Beachten Sie die Verweise in *"Project.JSON"*.
* Von der **Projektmappen-Explorer**, löschen Sie die *"Project.JSON"* Datei aus dem Projekt. Dies löscht die *"Project.JSON"* Datei, und entfernt sie aus dem Projekt.
* Fügen Sie dem Projekt die NuGet-Verweise in sichern:
    * Mit der rechten Maustaste auf die **Lösung** , und wählen Sie **NuGet-Pakete für Projektmappe verwalten**.
    * Visual Studio erstellt automatisch die *"Packages.config"* -Datei für Sie.

> [!NOTE]
> Wenn Ihr Projekt EnvDTE-Pakete enthalten, müssen sie möglicherweise hinzugefügt werden, indem Sie mit der rechten Maustaste auf **Verweise** auswählen **Verweis hinzufügen** und den entsprechenden Verweis hinzugefügt haben.  Mithilfe von NuGet-Pakete kann Fehler erstellen, bei dem Versuch, Ihr Projekt zu erstellen.

## <a name="add-appropriate-build-tools"></a>Hinzufügen der entsprechenden Build-tools

Um sicherzustellen, dass müssen Build-Tools hinzuzufügen, die können wir entwickeln und Debuggen Sie entsprechend. Microsoft hat eine Assembly für diese aufgerufene Microsoft.VisualStudio.Sdk.BuildTasks erstellt.

Zum Erstellen und Bereitstellen einer VSIXv3 in Visual Studio 2015 und 2017, müssen Sie die folgenden NuGet-Pakete:

Version | Integrierte Tools
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Gehen Sie hierzu wie folgt vor:

* Fügen Sie das NuGet-Paket Microsoft.VisualStudio.Sdk.BuildTasks.14.0 zu Ihrem Projekt hinzu.
* Wenn Ihr Projekt nicht Microsoft.VSSDK.BuildTools enthält, fügen Sie ihn aus.
* Sicherzustellen, dass die Version Microsoft.VSSDK.BuildTools 15.x oder höher.

## <a name="update-extension-manifest"></a>Erweiterungsmanifest für aktualisieren

### <a name="1-installation-targets"></a>1. Installationsziele

Wir müssen, um Visual Studio mitzuteilen, welche Versionen als Ziel für das Erstellen einer VSIX-Datei.  Diese Verweise sind in der Regel entweder mit der Version 14.0 (Visual Studio 2015) oder Version 15.0 (Visual Studio 2017).  In diesem Fall möchten wir eine VSIX erstellen, die eine Erweiterung für beide installiert wird, daher wir beide Versionen als Ziel müssen.  Wenn Sie möchten Ihre VSIX erstellen und installieren in Versionen vor 14.0, kann dies erfolgen durch Festlegen der Anzahl der früheren Version; Allerdings Version 10.0 und ältere Versionen werden nicht mehr unterstützt.

* Öffnen der *"Source.Extension.vsixmanifest"* Datei in Visual Studio.
* Öffnen der **Ziele installieren** Registerkarte.
* Ändern der **Versionsbereich** auf [14.0, 16,0).  Die ' [' teilt Visual Studio das 14.0 und alle Versionen fügen Sie ihn.  Die ')' teilt Visual Studio, um alle Versionen von 15.0 bis zur, aber nicht einschließlich Version 16.0 enthalten.
* Speichert alle Änderungen, und schließen Sie alle Instanzen von Visual Studio.

![Installationsabbilddatei (Ziele)](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Hinzufügen von Voraussetzungen für die *"Extension.vsixmanifest"* Datei

Voraussetzungen sind ein neues Feature in Visual Studio 2017.  In diesem Fall müssen wir die Visual Studio-Kern-Editor als erforderliche Komponente. Da der Visual Studio 2015-VSIX-Designer nicht des neuen behandeln `Prerequisites` Abschnitt müssen Sie diese Komponente in der XML-Code manuell bearbeiten.  Alternativ können Sie Visual Studio 2017 öffnen, und verwenden den aktualisierte Manifesten-Designer, um die erforderlichen Komponenten einzufügen.

Die CWL manuell erstellen:

* Navigieren Sie zu dem Verzeichnis des Projekts im Datei-Explorer.
* Öffnen der *"Extension.vsixmanifest"* -Datei mit einem Text-Editor.
* Fügen Sie das folgende Tag hinzu:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Speichern und schließen Sie die Datei.

> [!NOTE]
> Wenn Sie auswählen, um dies mit dem VSIX-Designer in Visual Studio 2017 zu erreichen, müssen Sie manuell bearbeiten, um sicherzustellen, dass er kompatibel mit allen Versionen von Visual Studio 2017 ist die erforderliche Version.  Dies ist, da der Designer die mindestens erforderliche Version als aktuelle Version von Visual Studio (z. B. 15.0.26208.0) eingefügt wird.  Da andere Benutzer möglicherweise eine frühere Version hat, möchten Sie jedoch werden dies manuell bearbeiten, bis 15.0 angibt.

An diesem Punkt sollte Ihre Manifestdatei etwa wie folgt aussehen:

![Beispiel für erforderliche Komponenten](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Ändern der Projektdatei (MyProject.csproj erstellt)

Es wird dringend empfohlen, um einen Verweis auf eine geänderte csproj geöffnet ist, während der Ausführung dieses Schritts zu erhalten.  Sie finden einige Beispiele für [hier](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Markieren Sie ein erweiterbarkeitsbeispiel, suchen die *csproj* -Datei für den Verweis, und führen Sie die folgenden Schritte aus:

* Navigieren Sie zu dem Projektverzeichnis in **Datei-Explorer**.
* Öffnen der *MyProject.csproj erstellt* -Datei mit einem Text-Editor.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Update the MinimumVisualStudioVersion

* Legen Sie die minimale visual Studio-Version auf `$(VisualStudioVersion)` , und fügen Sie dafür eine bedingte Anweisung hinzu.  Fügen Sie diese Tags hinzu, wenn sie nicht vorhanden sind.  Stellen Sie sicher, dass die Tags festgelegt sind, wie unten gezeigt:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Fügen Sie die VsixType-Eigenschaft hinzu.

* Fügen Sie das folgende Tag `<VsixType>v3</VsixType>` auf eine Eigenschaftengruppe.

> [!NOTE]
> Es wird empfohlen, die Hiermit unterhalb der `<OutputType></OutputType>` Tag.

### <a name="3-add-the-debugging-properties"></a>3. Fügen Sie die debugging-Eigenschaften

* Fügen Sie der Gruppe der folgenden Eigenschaften hinzu:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Löschen Sie alle Instanzen der im folgenden Codebeispiel wird von der *csproj* -Datei und alle *. csproj.user* Dateien:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Hinzufügen von Bedingungen auf der Build-Tools-Importe

* Fügen Sie zusätzliche bedingte Anweisungen, um die `<import>` Tags, die einen Verweis Microsoft.VSSDK.BuildTools verfügen.  Fügen Sie `'$(VisualStudioVersion)' != '14.0' And` am Anfang der bedingungsanweisung.  Diese Anweisungen werden in die Kopf- und Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Fügen Sie zusätzliche bedingte Anweisungen, um die `<import>` Tags, die eine Microsoft.VisualStudio.Sdk.BuildTasks.14.0 aufweisen. Fügen Sie `'$(VisualStudioVersion)' == '14.0' And` am Anfang der bedingungsanweisung. Diese Anweisungen werden in die Kopf- und Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Fügen Sie zusätzliche bedingte Anweisungen, um die `<Error>` Tags, die einen Verweis Microsoft.VSSDK.BuildTools verfügen.  Zu diesem Zweck einfügen `'$(VisualStudioVersion)' != '14.0' And` am Anfang der bedingungsanweisung. Diese Anweisungen werden in der Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Fügen Sie zusätzliche bedingte Anweisungen, um die `<Error>` Tags, die eine Microsoft.VisualStudio.Sdk.BuildTasks.14.0 aufweisen.  Fügen Sie `'$(VisualStudioVersion)' == '14.0' And` am Anfang der bedingungsanweisung. Diese Anweisungen werden in der Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Speichern Sie die Csproj-Datei, und schließen Sie sie.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Testen Sie die Erweiterung installiert, in Visual Studio 2015 und Visual Studio 2017

An diesem Punkt sollte Ihr Projekt bereit sein, eine VSIXv3 zu erstellen, die auf Visual Studio 2015 und Visual Studio 2017 installiert werden kann.

* Öffnen Sie Ihr Projekt in Visual Studio 2015.
* Erstellen Sie das Projekt, und vergewissern Sie sich in der Ausgabe, die einer VSIX-Datei richtig erstellt wird.
* Navigieren Sie zu Ihrem Projektverzeichnis.
* Öffnen der *\bin\Debug* Ordner.
* Doppelklicken Sie auf die VSIX-Datei, und installieren Sie die Erweiterung für Visual Studio 2015 und Visual Studio 2017.
* Stellen Sie sicher, dass Sie die Erweiterung in sehen **Tools** > **Erweiterungen und Updates** in die **installiert** Abschnitt.
* Es wurde versucht, ausführen und verwenden die Erweiterung, um sicherzustellen, dass es funktioniert.

![Suchen einer VSIX-Datei](media/finding-a-VSIX-example.png)

> [!NOTE]
> Wenn Ihr Projekt mit der Meldung hängt **Öffnen der Datei**, Herunterfahren erzwingen von Visual Studio, wechseln Sie zu Ihrem Projektverzeichnis, versteckte Ordner anzeigen und löschen die *.vs* Ordner.