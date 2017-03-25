---
title: Breaking Changes in Visual Studio 2017 Erweiterbarkeit | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Änderungen in Visual Studio 2017-Erweiterbarkeit

Mit Visual Studio 2017 bieten wir eine [schnellere, schlankere Erfahrung von Visual Studio-Installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) , die durch die Reduzierung von Visual Studio auf Benutzer-Systemen und größere Auswahl bietet den Benutzern über die Arbeitslasten und Features, die installiert werden. Um diese Verbesserungen unterstützen, wir das Erweiterbarkeitsmodell Änderungen vorgenommen haben und einige grundlegende Änderungen vorgenommen haben, um Visual Studio-Erweiterbarkeit. Dieses Dokument wird beschrieben, die technischen Details der diese Änderungen und Aktionen durchgeführt werden können, um diese zu beheben. Bitte beachten Sie, dass einige Implementierungsdetails von Point-in-Time und später geändert werden kann.

## <a name="changes-affecting-vsix-format-and-installation"></a>Änderungen, die VSIX-Format und die Installation beeinflussen

Wir bei der Einführung von der VSIX-v3-Format (Version 3) zur Unterstützung der Lightweight-Installation.

An das VSIX-Format enthalten:

* Die Deklaration der Setup-Komponenten. Zum Übermitteln von für die Zusage der einfache, schnelle Installation von Visual Studio bietet das Installationsprogramm jetzt mehr Konfigurationsoptionen für Benutzer. Daher sicherstellen, dass die Features und Komponenten, die erforderlich sind, von einer Erweiterung installiert sind, müssen Erweiterungen ihre Abhängigkeiten zu deklarieren.
  * Der Installer für Visual Studio 2017 bietet automatisch erwerben und installieren die erforderlichen Komponenten für den Benutzer im Rahmen der Installation der Erweiterungs.
  * Benutzer werden auch gewarnt, wenn Sie versuchen, eine Erweiterung zu installieren, die mit dem neuen VSIX-v3-Format nicht erstellt wurde, selbst wenn sie im Manifest als Version 15.0 Zielgruppenadressierung markiert wurden.
* Erweiterte Funktionen für das VSIX-Format. Die Bereitstellen einer [mit geringen Auswirkungen installieren](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) von Visual Studio, die Side-by-Side Installation ebenfalls unterstützt, wir nicht mehr speichern Sie die meisten Konfigurationsdaten in der Registrierung und Visual Studio-spezifischen Assemblys aus dem GAC verschoben haben. Wir erhöhten auch die Funktionen der VSIX-Format und des Moduls des VSIX-Installation, und Sie können es statt eine MSI- oder EXE-Datei verwenden, die Erweiterungen für einige Installationstypen installieren.

  Die neuen Funktionen gehören:

  * Die Registrierung in der angegebenen Instanz von Visual Studio.
  * Installation außerhalb der [Erweiterungsordner](set-install-root.md).
  * Erkennung von der Prozessorarchitektur.
  * Abhängigkeit von Sprache getrennte Sprachpakete.
  * Installation mit [NGEN-Unterstützung](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Erstellen eine Erweiterung für Visual Studio 2017

Designer-Tools für die Erstellung von neuen ist VSIX-v3-Manifestformat jetzt verfügbar in Visual Studio 2017. Finden Sie im Begleitdokument [wie: Erweiterungsprojekte migrieren, um Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) ausführliche Informationen über die Verwendung der Designer-Tools oder manuelle Aktualisierungen für das Projekt und das Manifest VSIX-v3-Erweiterungen zu entwickeln.

## <a name="change-visual-studio-user-data-path"></a>Ändern: Visual Studio Datenpfad

Früher konnte nur eine Installation der einzelnen Hauptversion von Visual Studio auf jedem Computer vorhanden sein. Zur Unterstützung von Seite-an-Seite-Installationen von Visual Studio 2017 möglicherweise mehrere benutzerdatenpfade für Visual Studio auf dem Computer des Benutzers vorhanden.

Innerhalb des Visual Studio-Prozess ausgeführte Code sollte aktualisiert werden, um Visual Studio Settings Manager verwenden. Außerhalb des Visual Studio-Prozess ausgeführte Code finde den Pfad einer bestimmten Visual Studio-Installation [anhand der Anleitung hier](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).

## <a name="change-global-assembly-cache-gac"></a>Ändern: Globaler Assemblycache (GAC)

Die meisten Visual Studio Core-Assemblys werden nicht mehr im globalen Assemblycache installiert. Die folgenden Änderungen vorgenommen wurden, sodass in Visual Studio-Prozess ausgeführte Code weiterhin erforderlichen Assemblys zur Laufzeit finden kann.

* Assemblys, die nur im globalen Assemblycache installiert wurden:
  * Diese Assemblys werden nun unter %VsFolder%\Common7\IDE installiert\, %VsFolder%\Common7\IDE\PublicAssemblies oder % VsFolder%\Common7\IDE\PrivateAssemblies. Diese Ordner sind Teil der Visual Studio-Prozess Prüfpfade.
* Assemblys, die in einem Pfad nicht überprüfen und im globalen Assemblycache installiert wurden:
  * Die Kopie im GAC wurde von Setup entfernt.
  * Eine PKGDEF-Datei wurde hinzugefügt, um eine CodeBase-Eintrag für die Assembly anzugeben.

    Zum Beispiel:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    Zur Laufzeit wird das Visual Studio Pkgdef-Subsystem diese Einträge in der Visual Studio-Prozess Common Language Runtime-Konfigurationsdatei (unter % VsAppDataFolder%\devenv.exe.config) als merge [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) Elemente. Dies ist die empfohlene Methode zum Visual Studio-Prozess, die Assembly zu suchen zu lassen, da es vermeidet probing Pfade durchsucht.

### <a name="reacting-to-this-breaking-change"></a>Reagieren auf diesen unterbrechende Änderung

* Wenn die Erweiterung in der Visual Studio-Prozess ausgeführt wird:
  * Der Code wird Visual Studio Core-Assemblys zu finden sein.
  * Erwägen Sie eine PKGDEF-Datei einen Pfad auf die Assemblys bei Bedarf angeben.
* Wenn die Erweiterung außerhalb der Visual Studio-Prozess ausgeführt wird:
  * Sehen Sie die für Visual Studio Core-Assemblys unter %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies oder %VsFolder%\Common7\IDE\PrivateAssemblies Konfiguration Datei- oder Assemblyname Konfliktlöser.

## <a name="change-reduce-registry-impact"></a>Änderung: Reduzieren der Auswirkungen der Registrierung

### <a name="global-com-registration"></a>Globale COM-Registrierung

* Zuvor installierte Visual Studio viele Registrierungsschlüssel in den Strukturen für HKEY_CLASSES_ROOT und HKEY_LOCAL_MACHINE systemeigene COM-Registrierung zu unterstützen. Um diese Auswirkung zu vermeiden, verwendet Visual Studio jetzt [Aktivierung ohne Registrierung ist für COM-Komponenten](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Folglich müssen die meisten TLB / OLB / DLL-Dateien unter % ProgramFiles% (x86) %\Common c:\Programme\Microsoft Shared\MSEnv werden nicht mehr standardmäßig von Visual Studio installiert. Diese Dateien werden unter % VsFolder mit entsprechenden Registration-Free COM-Manifeste, die von der Visual Studio-Hostprozess verwendet jetzt installiert.
* Daher findet externe Codes, globale COM-Registrierung für Visual Studio COM-Schnittstellen verwendet, nicht mehr diese Registrierungen. In Visual Studio-Prozess ausgeführte Code wird einen Unterschied nicht angezeigt.

### <a name="visual-studio-registry"></a>Visual Studio-Registrierung

* Zuvor installiert Visual Studio viele Registrierungsschlüssel in das System HKEY_LOCAL_MACHINE und HKEY_CURRENT_USER Strukturen unter einem Visual Studio-spezifische Schlüssel:
  * HKLM\Software\Microsoft\VisualStudio\\**Version**: Registrierungsschlüssel, die von MSI-Installationsprogramme und Erweiterungen pro Computer erstellt.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**: Registrierungsschlüssel, die von Visual Studio zum Speichern der benutzerspezifischen Einstellungen erstellt.
  * HKCU\Software\Microsoft\VisualStudio\\**Version**_Config: eine Kopie von Visual Studio HKLM-Taste oben, plus die Registrierungsschlüssel zusammengeführt PKGDEF-Dateien von Erweiterungen.
* Um die Auswirkung auf die Registrierung zu reduzieren, verwendet Visual Studio jetzt die [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) Funktion zum Speichern der Registrierungsschlüssel in einer privaten Binärdatei unter % VsAppDataFolder%\privateregistry.bin. Nur eine sehr kleine Anzahl von Visual Studio-spezifische Schlüssel bleiben in der Registrierung.
* Vorhandenen Code innerhalb des Visual Studio ausgeführt wird nicht beeinträchtigt. Visual Studio leitet alle Registrierungsoperationen unter dem Schlüssel "HKCU" Visual Studio-spezifische auf die private-Registrierung. Lesen und Schreiben in andere Registrierungsspeicherorte werden weiterhin die Registrierung verwenden.
* Externer Code müssen zu lesen und aus dieser Datei für Visual Studio-Registrierungseinträge.

### <a name="reacting-to-this-breaking-change"></a>Reagieren auf diesen unterbrechende Änderung

* Externer Code konvertiert werden sollen, um für COM-Komponenten sowie die Aktivierung ohne Registrierung verwenden.
* Externe Komponenten können der Speicherort von Visual Studio suchen [anhand der Anleitung hier](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Es wird empfohlen, externe Komponenten, die die [externe Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) anstelle von Lesen/Schreiben direkt in Visual Studio-Registrierungsschlüssel.
* Überprüfen Sie, ob die Komponenten, die die Erweiterung verwendet, wird eine andere Technik für die Registrierung implementiert haben können. Zum Beispiel möglicherweise Debuggererweiterungen Nutzen der neuen [Msvsmon JSON-Datei COM-Registrierung](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Ändern: Die einfache Lösung Last

Einfache Lösung laden (LSL) verringert, dass zum Laden der Projektmappe Projekte nicht vollständig geladen, bis der Benutzer mit ihnen arbeiten startet. Dies kann es sich um Erweiterungen auswirken wird angenommen, dass ein Projekt vollständig geladen wird. Finden Sie unter [Laden einer Projektmappe Lightweight](lightweight-solution-load-extension-impact.md) zur Feststellung, ob die Erweiterung wird möglicherweise beeinträchtigt werden, und erhalten einen Leitfaden zum Aktualisieren der Erweiterungs.

