---
title: "Wichtige Änderungen in Visual Studio 2017 Erweiterbarkeit | Microsoft Docs"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d474374a0c7603bc9b6995783bbed96c81c8907
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Änderungen in Visual Studio 2017-Erweiterbarkeit

Mit Visual Studio 2017 bieten wir eine [schneller und weniger umfangreiche Erfahrung von Visual Studio-Installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) , die durch die Reduzierung von Visual Studio auf Benutzersystemen, und bietet den Benutzern größer Wahl über die arbeitsauslastungen und -Funktionen installiert werden. Um diese Verbesserungen zu unterstützen, wir haben Änderungen vorgenommen, auf dem Erweiterungsmodell und einiger wesentlicher Änderungen vorgenommen haben, um Visual Studio-Erweiterbarkeit. Dieses Dokument beschreibt die technischen Details der diese Änderungen und welche Aktionen ausgeführt werden können, um zu begegnen. Bitte beachten Sie, dass einige Informationen Point-in-Time-Implementierungsdetails und möglicherweise später geändert werden.

## <a name="changes-affecting-vsix-format-and-installation"></a>Änderungen, die VSIX-Format und die Installation beeinflussen

Wir sind Einführung, in dem VSIX-v3-Format (Version 3) zur Unterstützung der Lightweight-Installation.

Änderungen an das VSIX-Format enthalten:

* Deklaration von setupvoraussetzungen. Zum Übermitteln von auf das Versprechen der eine einfache, schnelle Installation von Visual Studio bietet Installationsprogramm nun weitere Konfigurationsoptionen für Benutzer. Demzufolge, um sicherzustellen, dass die Features und Komponenten erforderlich sind, von einer Erweiterung installiert sind, müssen Erweiterungen ihre Abhängigkeiten zu deklarieren.
  * Der Installer für Visual Studio-2017 wird automatisch zum Abrufen und installieren die erforderlichen Komponenten für den Benutzer als Teil der Installation der Erweiterungs bieten.
  * Benutzer werden auch gewarnt, wenn Sie möchten, installieren Sie eine Erweiterung, die mit dem neuen VSIX-v3-Format nicht erstellt wurde, auch wenn sie in ihre Manifest als Version 15.0 Zielgruppenadressierung markiert wurden.
* Verbesserte Funktionen für das VSIX-Format. Zum Übermitteln von auf einem [mit geringen Auswirkungen installieren](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) von Visual Studio, die Seite-an-Seite installiert auch unterstützt, wir nicht mehr die meisten Konfigurationsdaten in der Registrierung speichern und Visual Studio-spezifische Assemblys aus dem GAC verschoben wurden. Wir erhöht auch die Funktionen des die VSIX-Format und das Modul für VSIX-Installation, und Sie können sie statt einer MSI-Datei oder EXE-Datei zum Installieren der Erweiterungen für einige Arten verwenden.

  Die neuen Funktionen zählen:

  * Registrierung in der angegebenen Instanz von Visual Studio.
  * Installation außerhalb der [Ordner "Extensions"](set-install-root.md).
  * Erkennung von der Prozessorarchitektur.
  * Abhängigkeit von Sprache getrennte Sprachpakete.
  * Installation mit [NGEN-Unterstützung](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Erstellen eine Erweiterung für Visual Studio-2017

Designer-Tools für die Erstellung der neuen ist VSIX-v3-Manifestformat jetzt verfügbar in Visual Studio 2017. Finden Sie im zugehörige Dokument [wie: Migrieren Erweiterungsprojekte zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) Einzelheiten zu den Designertools verwenden oder manuelle Aktualisierungen für das Projekt und Manifest, für das VSIX-v3-Erweiterungen entwickeln.

## <a name="change-visual-studio-user-data-path"></a>Ändern: Visual Studio Datenpfad

Zuvor konnte nur eine Installation der einzelnen Hauptversion von Visual Studio auf jedem Computer vorhanden sind. Zur Unterstützung von Seite-an-Seite-Installationen von Visual Studio 2017 möglicherweise mehrere benutzerdatenpfade für Visual Studio auf dem Computer des Benutzers vorhanden.

Code im Visual Studio-Prozess ausgeführt wird sollten aktualisiert werden, um dem Visual Studio-Einstellungen-Manager zu verwenden. Code außerhalb der Visual Studio-Prozess ausgeführt wird, kann den Benutzerpfad einer bestimmten Visual Studio-Installation suchen [anhand der Anleitungen im folgenden](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Ändern: Globaler Assemblycache (GAC)

Die meisten Visual Studio Core-Assemblys werden nicht mehr im globalen Assemblycache installiert. Die folgenden Änderungen wurden vorgenommen, sodass in Visual Studio-Prozess ausgeführte Code weiterhin erforderlichen Assemblys zur Laufzeit finden kann.

> [!NOTE]
> [INSTALLDIR] unten bezieht sich auf das Stammverzeichnis der Installation von Visual Studio. VSIXInstaller.exe wird automatisch das Auffüllen, aber benutzerdefinierte Bereitstellungscode schreiben und Lesen Sie [Suchen von Visual Studio](locating-visual-studio.md).

* Assemblys, die nur im globalen Assemblycache installiert wurden:
  * Diese Assemblys werden nun unter [INSTALLDIR] \Common7\IDE installiert\, [INSTALLDIR] \Common7\IDE\PublicAssemblies oder \Common7\IDE\PrivateAssemblies [INSTALLDIR]. Diese Ordner sind Teil der Visual Studio-Prozess Prüfpfade.
* Assemblys, die zu einem Pfad nicht probing und im globalen Assemblycache installiert wurden:
  * Die Kopie im globalen Assemblycache wurde über das Setup entfernt.
  * Eine PKGDEF-Datei wurde hinzugefügt, um eine CodeBase-Eintrag für die Assembly anzugeben.

    Zum Beispiel:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Zur Laufzeit wird das Visual Studio Pkgdef-Subsystem diese Einträge in der Visual Studio-Prozess Laufzeitkonfigurationsdatei (unter [VSAPPDATA]\devenv.exe.config) als merge [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) Elemente. Dies ist die empfohlene Methode, die Visual Studio-Prozess, der die Assembly zu suchen zu lassen, da Pfade probing durchsuchen vermieden werden.

### <a name="reacting-to-this-breaking-change"></a>Das reagieren auf diesen unterbrechende Änderung

* Wenn Ihre Erweiterung in der Visual Studio-Prozess ausgeführt wird:
  * Der Code wird möglicherweise Visual Studio Core-Assemblys zu finden sein.
  * Erwägen Sie eine PKGDEF-Datei auf einen Pfad zu Assemblys bei Bedarf angeben.
* Wenn die Erweiterung außerhalb der Visual Studio-Prozess ausgeführt wird:
  * Sehen Sie die für Visual Studio Core-Assemblys unter [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies oder [INSTALLDIR] \Common7\IDE\PrivateAssemblies Konfiguration Datei- oder Assemblyname Konfliktlöser.

## <a name="change-reduce-registry-impact"></a>Änderung: Reduzieren der Auswirkungen der Registrierung

### <a name="global-com-registration"></a>Globale COM-Registrierung

* Zuvor installiert Visual Studio viele Registrierungsschlüssel in der HKEY_CLASSES_ROOT und HKEY_LOCAL_MACHINE Strukturen um systemeigene COM-Registrierung zu unterstützen. Um diese Auswirkungen zu vermeiden, verwendet Visual Studio nun [registrierungsfreie Aktivierung für COM-Komponenten](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Demzufolge die meisten TLB / OLB / DLL-Dateien unter % ProgramFiles% (x86) %\Common c:\Programme\Microsoft Shared\MSEnv sind nicht mehr standardmäßig von Visual Studio installiert. Diese Dateien werden mit entsprechenden registrierungsfreie COM-Manifeste, die von der Visual Studio-Hostprozess verwendet jetzt unter [INSTALLDIR] installiert.
* Daher findet externen Code, der globale COM-Registrierung für Visual Studio-COM-Schnittstellen, nutzt, diese Registrierungen nicht mehr. In Visual Studio-Prozess ausgeführte Code wird einen Unterschied nicht angezeigt werden.

### <a name="visual-studio-registry"></a>Visual Studio-Registrierung

* Zuvor installiert Visual Studio viele Registrierungsschlüssel in das System HKEY_LOCAL_MACHINE und HKEY_CURRENT_USER Registrierungsstrukturen unter einem Visual Studio-spezifische Schlüssel:
  * HKLM\Software\Microsoft\VisualStudio\\**Version**: Registrierungsschlüssel erstellt, indem MSI-Installer und Erweiterungen pro Computer.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**: Registrierungsschlüssel erstellt, die von Visual Studio, um benutzerspezifische Einstellungen speichern.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**_Config: eine Kopie des oben genannten Visual Studio HKLM-Schlüssels sowie die Registrierungsschlüssel zusammengeführt PKGDEF-Dateien von Erweiterungen.
* Um die Auswirkungen auf die Registrierung zu reduzieren, verwendet Visual Studio nun die [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) Funktion zum Speichern der Registrierungsschlüssel in einer privaten Binärdatei unter [VSAPPDATA]\privateregistry.bin. Nur eine kleine Anzahl von Visual Studio-spezifische Schlüssel bleiben in der systemregistrierung.
* Vorhandenem Code im Visual Studio-Prozess ausgeführt wird, wird nicht beeinträchtigt. Visual Studio leitet alle Registrierungsvorgänge unter dem Schlüssel HKCU Visual Studio-spezifische auf die privaten Registrierung. Lesen und Schreiben in andere Registrierungsspeicherorte werden weiterhin die systemregistrierung verwenden.
* Externer Code müssen laden und aus dieser Datei für Visual Studio-Registrierungseinträge zu lesen.

### <a name="reacting-to-this-breaking-change"></a>Das reagieren auf diesen unterbrechende Änderung

* Externer Code konvertiert werden sollen, um für COM-Komponenten sowie Aktivierung ohne Registrierung verwenden.
* Externe Komponenten können den Visual Studio finden [anhand der Anleitungen im folgenden](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Es wird empfohlen, dass externe Komponenten verwenden die [externe Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) anstelle von Lesen/Schreiben direkt in Visual Studio-Registrierungsschlüssel.
* Überprüfen Sie, ob die Komponenten an, die die Erweiterung verwendet eine andere Technik für die Registrierung implementiert haben können. Z. B. möglicherweise Debuggererweiterungen nutzen die neuen [Msvsmon JSON-Datei COM-Registrierung](migrate-debugger-COM-registration.md).
