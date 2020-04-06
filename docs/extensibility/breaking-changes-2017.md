---
title: Brechen von Änderungen in Visual Studio 2017-Erweiterbarkeit
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739968"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Änderungen in Visual Studio 2017 Erweiterbarkeit

Visual Studio 2017 bietet eine [schnellere, leichtere Visual Studio-Installationsumgebung,](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) die die Auswirkungen von Visual Studio auf Benutzersysteme reduziert und den Benutzern eine größere Auswahl an Workloads und Features bietet, die installiert sind. Um diese Verbesserungen zu unterstützen, haben wir Änderungen am Erweiterbarkeitsmodell vorgenommen, einschließlich einiger brechender Änderungen. In diesem Artikel werden die technischen Details dieser Änderungen beschrieben und was getan werden kann, um sie zu beheben.

> [!NOTE]
> Einige Informationen sind Point-in-Time-Implementierungsdetails und können später geändert werden.

## <a name="changes-affecting-vsix-format-and-installation"></a>Änderungen im VSIX-Format und bei der Installation

Visual Studio 2017 führte das VSIX v3-Format (Version 3) ein, um die einfache Installation zu unterstützen.

Zu den Änderungen am VSIX-Format gehören:

* Deklaration der Setup-Voraussetzungen. Um das Versprechen eines leichten, schnell installierenden Visual Studio zu erfüllen, bietet das Installationsprogramm benutzern jetzt mehr Konfigurationsoptionen. Um sicherzustellen, dass die für eine Erweiterung erforderlichen Features und Komponenten installiert sind, müssen Erweiterungen daher ihre Abhängigkeiten deklarieren.

  * Das Visual Studio 2017-Installationsprogramm bietet automatisch an, die erforderlichen Komponenten für den Benutzer im Rahmen der Installation der Erweiterung zu erwerben und zu installieren.
  * Benutzer werden auch gewarnt, wenn sie versuchen, eine Erweiterung zu installieren, die nicht mit dem neuen VSIX v3-Format erstellt wurde, auch wenn sie in ihrem Manifest als Zielversion 15.0 markiert wurden.

* Erweiterte Funktionen für das VSIX-Format. Um eine [installation](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) mit geringen Auswirkungen von Visual Studio durchzuführen, die auch nebeneinander installierte Installationen unterstützt, speichern wir die meisten Konfigurationsdaten nicht mehr in der Systemregistrierung und haben Visual Studio-spezifische Assemblys aus dem GAC verschoben. Außerdem haben wir die Funktionen des VSIX-Formats und der VSIX-Installations-Engine erweitert, sodass Sie es anstelle eines MSI oder EXE verwenden können, um Ihre Erweiterungen für einige Installationstypen zu installieren.

Zu den neuen Funktionen gehören:

* Registrierung in der angegebenen Visual Studio-Instanz.
* Installation außerhalb des [Erweiterungsordners](set-install-root.md).
* Erkennung der Prozessorarchitektur.
* Abhängigkeit von sprachgetrennten Sprachpaketen.
* Installation mit [NGEN-Unterstützung](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Erstellen einer Erweiterung für Visual Studio 2017

Designer-Tools zum Erstellen des neuen VSIX v3-Manifestformats sind in Visual Studio 2017 verfügbar. Weitere Informationen zur Verwendung der Designertools oder zum Erstellen manueller Aktualisierungen des Projekts und des Manifests zum Entwickeln von VSIX v3-Erweiterungen finden Sie im Begleitdokument [Gewusst wie: Migrieren von Erweiterbarkeitsprojekten zu Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="change-visual-studio-user-data-path"></a>Änderung: Visual Studio-Benutzerdatenpfad

Bisher konnte nur eine Installation jeder Hauptversion von Visual Studio auf jedem Computer vorhanden sein. Um nebeneinander installierte Visual Studio 2017 zu unterstützen, sind möglicherweise mehrere Benutzerdatenpfade für Visual Studio auf dem Computer des Benutzers vorhanden.

Code, der im Visual Studio-Prozess ausgeführt wird, sollte aktualisiert werden, um den Visual Studio-Einstellungs-Manager zu verwenden. Code, der außerhalb des Visual Studio-Prozesses ausgeführt wird, kann den Benutzerpfad einer bestimmten Visual Studio-Installation finden, indem Sie [den Anweisungen hier](locating-visual-studio.md)folgen.

## <a name="change-global-assembly-cache-gac"></a>Änderung: Globaler Assemblycache (GAC)

Die meisten Visual Studio-Kernassemblys werden nicht mehr im GAC installiert. Die folgenden Änderungen wurden vorgenommen, damit Code, der im Visual Studio-Prozess ausgeführt wird, zur Laufzeit weiterhin erforderliche Assemblys finden kann.

> [!NOTE]
> [INSTALLDIR] unten bezieht sich auf das Installationsstammverzeichnis von Visual Studio. *VSIXInstaller.exe* wird dies automatisch auffüllen, aber um benutzerdefinierten Bereitstellungscode zu schreiben, lesen Sie bitte [Visual Studio .](locating-visual-studio.md)

* Assemblys, die nur im GAC installiert wurden:

  Diese Assemblys werden jetzt unter <em>\*[INSTALLDIR]-Common7-IDE , *[INSTALLDIR]-Common7-IDE-PublicAssemblies</em> oder *[INSTALLDIR]-Common7-IDE-PrivateAssemblies*installiert. Diese Ordner sind Teil der Suchpfade des Visual Studio-Prozesses.

* Assemblys, die in einem Nicht-Sondierungspfad und im GAC installiert wurden:

  * Die Kopie im GAC wurde aus dem Setup entfernt.
  * Eine *.pkgdef-Datei* wurde hinzugefügt, um einen Codebasiseintrag für die Assembly anzugeben.

    Beispiel:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Zur Laufzeit führt das Visual Studio-Subsystem pkgdef diese Einträge in der Laufzeitkonfigurationsdatei des Visual Studio-Prozesses (unter *[VSAPPDATA]-devenv.exe.config*) als [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) Elemente zusammen. Dies ist die empfohlene Methode, damit der Visual Studio-Prozess Ihre Assembly finden kann, da die Suche nach Suchpfaden vermieden wird.

### <a name="reacting-to-this-breaking-change"></a>Reaktion auf diesen brechenden Wandel

* Wenn Ihre Erweiterung im Visual Studio-Prozess ausgeführt wird:

  * Ihr Code kann Visual Studio-Kernassemblys finden.
  * Erwägen Sie die Verwendung einer *.pkgdef-Datei,* um bei Bedarf einen Pfad zu Ihren Assemblys anzugeben.

* Wenn Ihre Erweiterung außerhalb des Visual Studio-Prozesses ausgeführt wird:

  Erwägen Sie, Visual Studio-Kernassemblys unter <em>[INSTALLDIR]-Common7-IDE\*, *[INSTALLDIR]-Common7-IDE-PublicAssemblies</em> oder *[INSTALLDIR]* zu suchen, die eine Konfigurationsdatei oder einen Assembly-Resolver verwenden.

## <a name="change-reduce-registry-impact"></a>Änderung: Reduzieren der Auswirkungen auf die Registrierung

### <a name="global-com-registration"></a>Globale COM-Registrierung

* Zuvor hat Visual Studio viele Registrierungsschlüssel in den HKEY_CLASSES_ROOT installiert und HKEY_LOCAL_MACHINE Aufarbeitungen zur Unterstützung der systemeigenen COM-Registrierung. Um diese Auswirkungen zu vermeiden, verwendet Visual Studio jetzt [registrierungsfreie Aktivierung für COM-Komponenten](https://msdn.microsoft.com/library/ms973913.aspx).
* Daher werden die meisten TLB /OLB / DLL-Dateien unter %ProgramFiles(x86)%-Common Files-Microsoft Shared-MSEnv standardmäßig nicht mehr von Visual Studio installiert. Diese Dateien werden nun unter [INSTALLDIR] mit entsprechenden registrierungsfreien COM-Manifesten installiert, die vom Visual Studio-Hostprozess verwendet werden.
* Daher findet externer Code, der auf der globalen COM-Registrierung für Visual Studio COM-Schnittstellen basiert, diese Registrierungen nicht mehr. Code, der im Visual Studio-Prozess ausgeführt wird, sieht keinen Unterschied.

### <a name="visual-studio-registry"></a>Visual Studio-Registrierung

* Zuvor hat Visual Studio viele Registrierungsschlüssel in den **HKEY_LOCAL_MACHINE** und **HKEY_CURRENT_USER-Strukturen** des Systems unter einem Visual Studio-spezifischen Schlüssel installiert:

  * **HKLM-Software-Microsoft-VisualStudio-Version:\{** Registrierungsschlüssel, die von MSI-Installationsprogrammen und Pro-Computer-Erweiterungen erstellt wurden.
  * **HKCU-Software-Microsoft-VisualStudio-Version:\{** Registrierungsschlüssel, die von Visual Studio zum Speichern benutzerspezifischer Einstellungen erstellt wurden.
  * **HKCU-Software-Microsoft-VisualStudio-Version\{_Config**: Eine Kopie des Visual Studio HKLM-Schlüssels oben sowie die Registrierungsschlüssel, die von *.pkgdef-Dateien* durch Erweiterungen zusammengeführt werden.

* Um die Auswirkungen auf die Registrierung zu reduzieren, verwendet Visual Studio jetzt die [RegLoadAppKey-Funktion,](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) um Registrierungsschlüssel in einer privaten Binärdatei unter *[VSAPPDATA] zu speichern.* Nur eine sehr kleine Anzahl von Visual Studio-spezifischen Schlüsseln verbleibt in der Systemregistrierung.
* Vorhandener Code, der im Visual Studio-Prozess ausgeführt wird, hat keine Auswirkungen darauf. Visual Studio leitet alle Registrierungsvorgänge unter dem HKCU Visual Studio-spezifischen Schlüssel an die private Registrierung um. Das Lesen und Schreiben an andere Registrierungsspeicherorte wird weiterhin in der Systemregistrierung verwendet.
* Externer Code muss diese Datei für Visual Studio-Registrierungseinträge laden und aus dieser Datei lesen.

### <a name="react-to-this-breaking-change"></a>Reagieren Sie auf diese brechende Veränderung

* Externer Code sollte konvertiert werden, um die registrierungsfreie Aktivierung auch für COM-Komponenten zu verwenden.
* Externe Komponenten können den Visual Studio-Speicherort finden, indem Sie [die Anleitung hier befolgen.](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)
* Es wird empfohlen, dass externe Komponenten den [externen Einstellungs-Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) verwenden, anstatt direkt in Visual Studio-Registrierungsschlüssel zu lesen/schreiben.
* Überprüfen Sie, ob die Komponenten, die Ihre Erweiterung verwendet, möglicherweise eine andere Technik für die Registrierung implementiert haben. Beispielsweise können Debuggererweiterungen die neue [MSvsmon JSON-Datei COM-Registrierung](migrate-debugger-COM-registration.md)nutzen.
