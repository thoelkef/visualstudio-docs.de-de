---
title: Wichtige Änderungen in Visual Studio 2017-Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5305a5fd5dea53554e4ac9c0015e8181d5906788
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841949"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Änderungen in Visual Studio 2017-Erweiterbarkeit

Mit Visual Studio 2017, bieten wir eine [schnellere und schlankere Visual Studio-Installationsvorgang](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) , die durch die Reduzierung von Visual Studio auf Benutzersystemen und bietet den Benutzern mehr Auswahlmöglichkeiten über die arbeitsauslastungen und Features installiert werden. Um diese Verbesserungen zu unterstützen, wir Änderungen vorgenommen haben, für das Erweiterbarkeitsmodell und einige wichtige Änderungen an Visual Studio-Erweiterungen vorgenommen haben. In diesem Dokument wird beschrieben, die technischen Details dieser Änderungen, und was getan werden, um ihnen zu begegnen. Bitte beachten Sie, dass einige Informationen Point-in-Time-Implementierungsdetails und später nicht geändert werden kann.

## <a name="changes-affecting-vsix-format-and-installation"></a>Änderungen, die Auswirkungen auf die VSIX-Format und installation

Wir einführen, die VSIX-v3-Format (Version 3) zur Unterstützung der Lightweight-installationserfahrung.

Änderungen an das VSIX-Format enthalten:

* Die Deklaration der setupvoraussetzungen. Zum Übermitteln von die Vorzüge der eine einfache, schnelle Installation von Visual Studio bietet der Installer jetzt weitere Konfigurationsoptionen für Benutzer. Daher werden um sicherzustellen, dass die Features und Komponenten, die erforderlich sind, indem Sie eine Erweiterung installiert sind, Erweiterungen müssen ihre Abhängigkeiten deklarieren.
  * Das Visual Studio 2017-Installationsprogramm wird automatisch zum Abrufen und installieren die erforderlichen Komponenten für den Benutzer als Teil der Erweiterungsinstallation bieten.
  * Benutzer werden auch gewarnt, wenn Sie versuchen, eine Erweiterung zu installieren, die das neue VSIX v3-Format mit nicht erstellt wurde, auch wenn sie in deren Manifest als Ziel Version 15.0 markiert wurden.
* Erweiterte Funktionen für das VSIX-Format. Für die Einführung einer [mit geringen Auswirkungen Installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) von Visual Studio, die auch die Seite-an-Seite-Installationen unterstützt, wird nicht mehr speichern die meisten Konfigurationsdaten in die systemregistrierung und zusätzlichen Wartungsversionen wird Visual Studio-spezifische Assemblys aus dem GAC. Wir haben auch die Funktionen des VSIX-Format und VSIX-Installations-Engine, sodass Sie sie statt einer MSI oder EXE-Datei verwenden, um Ihre Erweiterungen für einige Installationstypen zu installieren.

  Die neuen Funktionen gehören:

  * Die Registrierung der angegebenen Instanz von Visual Studio.
  * Installationen außerhalb der [Ordner "Extensions"](set-install-root.md).
  * Erkennung von der Prozessorarchitektur.
  * Abhängigkeit von Sprache getrennte Sprachpakete.
  * Installation mit [Support für NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Erstellen eine Erweiterung für Visual Studio 2017

Designer-Tools für die Erstellung des neuen ist v3 VSIX-Manifestformat jetzt verfügbar in Visual Studio 2017. Finden Sie im Begleitdokument [Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) Einzelheiten der Verwendung der Designer-Tools oder manuelle Updates in das Projekt und das Manifest in VSIX v3-Erweiterungen zu entwickeln.

## <a name="change-visual-studio-user-data-path"></a>Ändern Sie: Visual Studio-benutzerdatenpfad

Bisher konnte nur eine Installation der einzelnen Hauptversionen von Visual Studio auf jedem Computer vorhanden sind. Zur Unterstützung von Seite-an-Seite-Installationen von Visual Studio 2017 möglicherweise mehrere benutzerdatenpfade für Visual Studio auf dem Computer des Benutzers vorhanden.

Im Visual Studio-Prozess ausgeführten Code sollte aktualisiert werden, um dem Visual Studio-Einstellungen-Manager zu verwenden. Code außerhalb von Visual Studio-Prozesses ausgeführt werden kann den Benutzerpfad Suchen einer bestimmten Visual Studio-Installation [anhand der Anleitungen hier](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Ändern Sie: Globaler Assemblycache (GAC)

Die meisten Visual Studio Core-Assemblys werden nicht mehr im globalen Assemblycache installiert. Die folgenden Änderungen wurden vorgenommen, sodass in Visual Studio-Prozess ausgeführte Code weiterhin erforderlichen Assemblys zur Laufzeit finden kann.

> [!NOTE]
> [INSTALLDIR] im folgenden in das Stammverzeichnis der Installation von Visual Studio verweist. *VSIXInstaller.exe* wird dies automatisch zu füllen, aber um benutzerdefiniertem Code zu schreiben, lesen Sie [finden von Visual Studio](locating-visual-studio.md).

* Assemblys, die nur im globalen Assemblycache installiert wurden:
  * Diese Assemblys sind jetzt installiert <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> oder *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Diese Ordner sind Teil der Visual Studio-Prozess Überprüfungspfade.

* Assemblys, die in einen Pfad ohne Überprüfung und im globalen Assemblycache installiert wurden:
  * Die Kopie im globalen Assemblycache wurde über das Setup entfernt.
  * Ein *PKGDEF* Datei wurde hinzugefügt, um eine CodeBase-Eintrag für die Assembly anzugeben.

    Zum Beispiel:

    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Zur Laufzeit führt das Visual Studio-Pkgdef-Subsystem zusammen diese Einträge in der Visual Studio-Prozess-Laufzeitkonfigurationsdatei (unter *[VSAPPDATA]\devenv.exe.config*) als [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) Elemente. Dies ist die empfohlene Methode zum Visual Studio-Prozesses finden Sie die Assembly, zu ermöglichen, da es verhindert die Überprüfung von Pfaden zu durchsuchen.

### <a name="reacting-to-this-breaking-change"></a>Reagieren auf diese wichtige Änderung

* Wenn Ihre Erweiterung in Visual Studio-Prozesses ausgeführt wird:
  * Der Code wird Visual Studio Core-Assemblys zu finden sein.
  * Erwägen Sie die Verwendung einer *PKGDEF* Datei, um einen Pfad auf die Assemblys bei Bedarf anzugeben.
* Wenn Ihre Erweiterung außerhalb der Visual Studio-Prozess ausgeführt wird:
  * Sehen Sie die für Visual Studio Core-Assemblys unter <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> oder *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*mithilfe von Konfiguration-Datei oder Assembly-Auflösung.

## <a name="change-reduce-registry-impact"></a>Ändern Sie: Reduzieren der Auswirkungen der Registrierung

### <a name="global-com-registration"></a>Globale COM-Registrierung

* Zuvor installierte Visual Studio viele Registrierungsschlüssel, in der HKEY_CLASSES_ROOT und HKEY_LOCAL_MACHINE-Strukturen, um systemeigene COM-Registrierung zu unterstützen. Um diese Auswirkungen zu vermeiden, verwendet Visual Studio jetzt [Aktivierung für COM-Komponenten ohne Registrierung](https://msdn.microsoft.com/library/ms973913.aspx).
* Als Ergebnis die meisten TLB / OLB / DLL-Dateien unter % ProgramFiles% (x86) %\Common c:\Programme\Microsoft Shared\MSEnv werden nicht mehr standardmäßig installiert, von Visual Studio. Diese Dateien werden mit entsprechenden COM ohne Registrierung Manifeste, die von der Visual Studio-Hostprozess verwendet jetzt unter [INSTALLDIR] installiert.
* Daher werden diese Registrierungen von externer Code, der globale COM-Registrierung für Visual Studio COM-Schnittstellen verwendet nicht mehr feststellen. In Visual Studio-Prozess ausgeführte Code wird eine Differenz nicht angezeigt.

### <a name="visual-studio-registry"></a>Visual Studio-Registrierung

* Visual Studio installiert zuvor viele Registrierungsschlüssel des Systems **HKEY_LOCAL_MACHINE** und **HKEY_CURRENT_USER** Strukturen unter einem Visual Studio-spezifischer Schlüssel:
  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Der Registrierungsschlüssel von MSI-Installationsprogramme und pro Computer Erweiterungen erstellt werden.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Der Registrierungsschlüssel erstellt, die von Visual Studio benutzerspezifische Einstellungen speichern.
  * **HKCU\Software\Microsoft\VisualStudio\{Version} _Config**: Eine Kopie von Visual Studio-HKLM-Taste oben, und die Registrierungsschlüssel vom zusammengeführt *PKGDEF* Dateien von Erweiterungen.
* Um die Auswirkungen auf die Registrierung zu reduzieren, verwendet Visual Studio jetzt die [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) Funktion zum Speichern von Registrierungsschlüssel in einer privaten Binärdatei unter *[VSAPPDATA]\privateregistry.bin*. Nur eine sehr kleine Anzahl von Visual Studio-spezifischer Schlüssel bleiben in der systemregistrierung.

* Vorhandenem Code innerhalb des Visual Studio ausgeführt wird nicht beeinträchtigt. Visual Studio werden alle Registrierungsvorgängen unter dem HKCU Visual Studio-spezifischer Schlüssel in die private Registrierung umgeleitet werden. Lesen und Schreiben in andere Registrierungsspeicherorte werden weiterhin die Registrierung des Systems verwenden.
* Externer Code müssen zum Laden und Lesen aus dieser Datei für Visual Studio-Registrierungseinträge.

### <a name="reacting-to-this-breaking-change"></a>Reagieren auf diese wichtige Änderung

* Externer Code konvertiert werden sollen, um für COM-Komponenten sowie Aktivierung ohne Registrierung zu verwenden.
* Externe Komponenten können den Speicherort von Visual Studio suchen [anhand der Anleitungen hier](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Es wird empfohlen, dass externe Komponenten verwenden die [externe Settings Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) anstelle von lesen/schreiben, direkt in Visual Studio-Registrierungsschlüssel.
* Überprüfen Sie, ob der Komponenten, die Ihre Erweiterung verwendet ein anderes Verfahren für die Registrierung implementiert haben können. Z. B. möglicherweise Debuggererweiterungen nutzen die neuen ["msvsmon" JSON-Datei-COM-Registrierung](migrate-debugger-COM-registration.md).
