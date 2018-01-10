---
title: "Vorgehensweise: Roundtrip-Erweiterungen für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload: willbrown
ms.openlocfilehash: b51673daa7a8c3526ad7de7f7cfdeac6a91d3b4b
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Vorgehensweise: Erweiterungen mit Visual Studio 2017 und Visual Studio 2015 kompatibel zu machen

Dieses Dokument erläutert, wie Erweiterungsprojekte Roundtrip zwischen Visual Studio 2015 und Visual Studio 2017 getroffen. Nachdem das Upgrade abgeschlossen wurde, werden ein Projekt öffnen, erstellen, installieren und in Visual Studio 2015 und Visual Studio 2017 ausführen können.  Als Referenz, einige Erweiterungen, die einen Roundtrip zwischen Visual Studio 2015 und Visual Studio 2017 können verwendbaren [hier](https://github.com/Microsoft/VSSDK-Extensibility-Samples) in Beispielen der Microsoft-Erweiterbarkeit.

Wenn Sie nur in Visual Studio 2017 erstellen, jedoch die Ausgabe der VSIX in Visual Studio 2015 und Visual Studio 2017 ausführen möchten, klicken Sie dann finden Sie in der [Erweiterung Migration Dokument](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Hinweis:** aufgrund von Änderungen in Visual Studio zwischen Versionen, einige Aspekte, die in einer Version gearbeitet hat funktioniert nicht, eine andere. Stellen Sie sicher, dass die Funktionen, die Sie aufrufen möchten in beiden Versionen verfügbar sind, oder die Erweiterung wird unerwartete Ergebnisse.

Hier wird ein Überblick über die Schritte, die Sie in diesem Dokument für den roundtripvorgang einer VSIX ausführen müssen:

1. Importieren Sie die richtige NuGet-Pakete.
2. Aktualisieren Sie Erweiterungsmanifest:
    * Installationsziel
    * Erforderliche Komponenten
3. Aktualisieren Sie die CSProj:
    * Update `<MinimumVisualStudioVersion>`.
    * Hinzufügen der `<VsixType>` Eigenschaft.
    * Fügen Sie die Eigenschaft Debuggen `($DevEnvDir)` 3 Mal.
    * Fügen Sie Bedingungen für das Importieren von Build-Tools und -Ziele.

4. Erstellen und testen

## <a name="environment-setup"></a>Umgebungssetup

Dieses Dokument wird davon ausgegangen, dass Sie Folgendes auf dem Computer installiert sein:

* Visual Studio 2015 mit dem VS-SDK installiert
* Visual Studio 2017 Arbeitslast Erweiterbarkeit installiert

## <a name="recommended-approach"></a>Empfohlene Vorgehensweise

Es wird dringend empfohlen, um das Upgrade mit Visual Studio 2015 wird anstelle von Visual Studio 2017 zu starten. Der Hauptvorteil bei der Entwicklung in Visual Studio 2015 wird sichergestellt, dass Sie nicht auf Assemblys verweisen, die nicht in Visual Studio 2015 verfügbar sind. Stimmen Sie die Entwicklung in Visual Studio 2017 besteht das Risiko, die Sie möglicherweise eine Abhängigkeit zu einer Assembly einführen, die nur in Visual Studio 2017 vorhanden ist.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Stellen Sie sicher, dass es ist kein Verweis auf die Datei "Project.JSON"

Weiter unten in diesem Dokument wird bedingte Import-Anweisungen in der Datei *.csproj eingefügt.  Dies funktioniert nicht, wenn die NuGet-Verweise in "Project.JSON" gespeichert werden. Daher sollten sie alle Verweise von NuGet auf die Datei "Packages.config" zu verschieben.
Wenn Ihr Projekt eine Datei "Project.JSON" enthält:

* Notieren Sie die Verweise in "Project.JSON" hinzu.
* Löschen Sie im Projektmappen-Explorer die Datei "Project.JSON" aus dem Projekt ein.
    * Hierdurch wird die Datei "Project.JSON" gelöscht, und entfernen es aus dem Projekt.
* Fügen Sie die NuGet-Verweise dem Projekt wieder hinzu.
    * Mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete für Projektmappe verwalten...**
    * Visual Studio erstellt die Datei "Packages.config" automatisch für Sie

>**Hinweis:** Wenn Ihr Projekt EnvDTE-Pakete enthalten, müssen sie möglicherweise hinzugefügt werden, indem Sie mit der mit der rechten Maustaste auf **Verweise** auswählen **Verweis hinzufügen** und den entsprechenden Verweis hinzufügen.  Mithilfe von NuGet-Pakete möglicherweise Fehler erstellen, beim Versuch, Ihr Projekt zu erstellen.

## <a name="adding-appropriate-build-tools"></a>Hinzufügen der entsprechenden Build-tools

Wir müssen sicherstellen, dass Buildtools hinzufügen, die wir erstellen und Debuggen von entsprechend ermöglichen. Microsoft hat es sich um eine Assembly für diese aufgerufene Microsoft.VisualStudio.Sdk.BuildTasks erstellt.

Zum Erstellen und Bereitstellen einer VSIXv3 in Visual Studio 2015 und 2017, benötigen Sie die folgenden NuGet-Pakete:

Version | Integrierte Tools
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Dazu:

* Fügen Sie dem Projekt das NuGet-Paket Microsoft.VisualStudio.Sdk.BuildTasks.14.0 hinzu.
* Wenn Ihr Projekt keine Microsoft.VSSDK.BuildTools enthält, fügen Sie ihn aus.
* Sicherzustellen, dass die Version Microsoft.VSSDK.BuildTools 15.x oder höher.

## <a name="update-extension-manifest"></a>Aktualisieren der Erweiterungsmanifest

### <a name="1-installation-targets"></a>1. Installationsziele

Wir müssen Visual Studio mitteilen, welche Versionen als Ziel für die Erstellung einer VSIX ist.  Diese Verweise sind in der Regel entweder mit der Version 14.0 (Visual Studio 2015) oder Version 15.0 (Visual Studio 2017).  In unserem Fall möchten wir eine VSIX erstellen, die eine Erweiterung für beide installiert wird, damit wir beide Versionen abzielen möchten.  Wenn Sie möchten Ihre VSIX erstellt und in Versionen vor 14.0 installiert, kann dies erfolgen durch Festlegen der früheren Versionsnummer; Allerdings Version 10.0 und früher werden nicht mehr unterstützt.

* Öffnen Sie die Datei "Source.Extension.vsixmanifest" in Visual Studio.
* Öffnen der **Ziele installieren** Registerkarte.
* Ändern der **Versionsbereich** auf [14.0, 16,0).  Die "[" Visual Studio angewiesen 14.0 und alle Versionen hinaus enthalten.  Die ")" weist Visual Studio, um alle Versionen von 15.0 bis zur, aber nicht einschließlich Version 16,0 einzubeziehen.
* Speichert alle Änderungen, und schließen Sie alle Instanzen von Visual Studio.

![Ziele Installationsabbild](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Hinzufügen von erforderlichen Komponenten auf die Datei "Extension.vsixmanifest"

Erforderliche Komponenten sind ein neues Feature in Visual Studio 2017.  In diesem Fall müssen wir die Core-Editor von Visual Studio als erforderliche Komponente. Da der Visual Studio 2015 VSIX-Designer nicht des neuen behandeln `Prerequisites` Abschnitt müssen Sie diesen Teil in der XML-Code manuell bearbeiten.  Alternativ können Sie Visual Studio 2017 öffnen und aktualisierte Manifesten-Designer verwenden, um die erforderlichen Komponenten zu einzufügen.

Um dies manuell tun:

* Navigieren Sie in das Projektverzeichnis im Datei-Explorer.
* Öffnen der `extension.vsixmanifest` -Datei mit einem Text-Editor.
* Fügen Sie das folgende Tag hinzu:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Speichern und schließen Sie die Datei.

>**Hinweis:** Falls gewünscht, um dies mit dem VSIX-Designer in Visual Studio 2017 zu erreichen, müssen Sie manuell bearbeiten, die erforderliche Version aus, um sicherzustellen, dass die kompatibel mit allen Versionen von Visual Studio 2017.  Dies ist, da der Designer die Mindestversion als Ihrer aktuellen Version von Visual Studio (z. B. 15.0.26208.0) eingefügt wird.  Da andere Benutzer eine frühere Version aufweisen können, möchten Sie jedoch werden dies manuell bearbeiten, um 15.0.

An diesem Punkt sollte die Manifestdatei etwa wie folgt aussehen:

![Beispiel für erforderliche Komponenten](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Ändern der Projektdatei (MyProject.csproj erstellt)

Es wird dringend empfohlen, einen Verweis auf eine geänderte csproj geöffnet ist, während Sie diesen Schritt ausführen.  Sie finden einige Beispiele für [hier](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Wählen Sie ein Beispiel für Erweiterbarkeit, suchen Sie die CSPROJ-Datei für den Verweis, und führen Sie die folgenden Schritte aus:

* Navigieren Sie in das Projektverzeichnis im Datei-Explorer.
* Öffnen Sie die Datei MyProject.csproj erstellt, mit einem Text-Editor.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aktualisieren Sie die MinimumVisualStudioVersion

* Legen Sie die minimale visual Studio-Version auf `$(VisualStudioVersion)` und fügen Sie dafür eine bedingte Anweisung hinzu.  Fügen Sie diese Tags hinzu, wenn sie nicht vorhanden sind.  Stellen Sie sicher, dass die Tags wie folgt festgelegt sind:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Fügen Sie die VsixType-Eigenschaft

* Fügen Sie das folgende Tag `<VsixType>v3</VsixType>` zu einer Eigenschaftengruppe.

>**Hinweis:** es wird empfohlen, diese hinzufügen unterhalb der `<OutputType></OutputType>` Tag.

### <a name="3-add-the-debugging-properties"></a>3. Fügen Sie die Debugeigenschaften

* Fügen Sie die folgende Eigenschaftengruppe hinzu:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Löschen Sie alle Instanzen der folgenden von der CSPROJ-Datei und alle. csproj.user-Dateien:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Hinzufügen von Bedingungen auf den Build-Tools-Importe

* Zusätzliche bedingte Anweisungen zum Hinzufügen der `<import>` Tags, die einen Verweis Microsoft.VSSDK.BuildTools verfügen.  Zu diesem Zweck einfügen `'$(VisualStudioVersion)' != '14.0' And` an den Anfang der bedingungsanweisung.  Diese Anweisungen werden in der Kopf- und Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Zusätzliche bedingte Anweisungen zum Hinzufügen der `<import>` Tags, die eine Microsoft.VisualStudio.Sdk.BuildTasks.14.0 haben.  Zu diesem Zweck einfügen `'$(VisualStudioVersion)' == '14.0' And` an den Anfang der bedingungsanweisung. Diese Anweisungen werden in der Kopf- und Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Zusätzliche bedingte Anweisungen zum Hinzufügen der `<Error>` Tags, die einen Verweis Microsoft.VSSDK.BuildTools verfügen.  Zu diesem Zweck einfügen `'$(VisualStudioVersion)' != '14.0' And` an den Anfang der bedingungsanweisung. Diese Anweisungen werden in der Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Zusätzliche bedingte Anweisungen zum Hinzufügen der `<Error>` Tags, die eine Microsoft.VisualStudio.Sdk.BuildTasks.14.0 haben.  Zu diesem Zweck einfügen `'$(VisualStudioVersion)' == '14.0' And` an den Anfang der bedingungsanweisung. Diese Anweisungen werden in der Fußzeile der Csproj-Datei angezeigt.

Zum Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Speichern Sie die Csproj-Datei, und schließen Sie es.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Testen Sie die Installation der Erweiterung in Visual Studio 2015 und Visual Studio 2017

Das Projekt sollte an diesem Punkt bereit für ein VSIXv3 zu erstellen, die auf Visual Studio 2015 und Visual Studio 2017 installieren können.

* Öffnen Sie das Projekt in Visual Studio 2015
* Erstellen Sie das Projekt, und vergewissern Sie sich in der Ausgabe, die ordnungsgemäß erstellt wird, eine VSIX
* Navigieren Sie zum Projektverzeichnis
* Öffnen der "bin" -> Debugordner
* Klicken Sie mit der Doppelklicken auf die VSIX-Datei, und installieren Sie die Erweiterung für Visual Studio 2015 und Visual Studio 2017
* Stellen Sie sicher, dass Sie die Erweiterung in Tools-Erweiterungen und Updates im Abschnitt "Installiert" > anzeigen können.
* Versucht, die Erweiterung aus, um zu überprüfen, dass er funktioniert Ausführen/verwenden

![Suchen nach einer VSIX](media/finding-a-VSIX-example.png)

>**Hinweis:** , wenn das Projekt mit der "Nachricht"Öffnen der Datei"Force" Herunterfahren von Visual Studio stürzt ab, navigieren Sie zum Projektverzeichnis, versteckte Ordner anzeigen und löschen Sie den VS-Ordner.
