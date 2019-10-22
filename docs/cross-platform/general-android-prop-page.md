---
title: Allgemeine Projekteigenschaften (Android C++) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4526a329b4e047a449995b7b5ef66362aff1cc8f
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950588"
---
# <a name="general-project-properties-android-c"></a>Allgemeine Projekteigenschaften (Android C++)

Eigenschaft | BESCHREIBUNG | Auswahlmöglichkeiten
--- | ---| ---
Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Target Name | Gibt einen Dateinamen an, den dieses Projekt generiert.
Zielerweiterung | Gibt eine Dateierweiterung an, die dieses Projekt generiert. (Beispiel: *.exe* oder *.dll*)
Bei der Bereinigung zu löschende Erweiterungen | Durch Semikolons getrennte Platzhalterspezifikation, die angibt, welche Dateien im Zwischenverzeichnis beim Bereinigen oder erneuten Erstellen gelöscht werden sollen.
Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist.
Plattformtoolset | Gibt das Toolset zum Erstellen der aktuellen Konfiguration an. Wenn keine Angabe erfolgt, wird das Standardtoolset verwendet.
Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)** : Dynamische Bibliothek ( *.so*)<br>**Statische Bibliothek (.a)** : Statische Bibliothek ( *.a*)<br>**Hilfsprogramm**: Hilfsprogramm<br>**Makefile**: Makefile<br>
API-Zielebene | API-Ebene des Android NDK, die diese Konfiguration als Ziel hat.
Verwendung von STL | Gibt an, welche C++-Standardbibliothek für diese Konfiguration verwendet werden soll. | **Minimale C++-Laufzeitbibliothek (system)**<br>**C++-Laufzeit statische Bibliothek (gabi++_static)**<br>**C++-Laufzeit freigegebene Bibliothek (gabi++_shared)**<br>**STLport-Laufzeit statische Bibliothek (stlport_static)**<br>**STLport-Laufzeit freigegebene Bibliothek (stlport_shared)**<br>**GNU STL statische Bibliothek (gnustl_static)**<br>**GNU STL freigegebene Bibliothek (gnustl_shared)**<br>**LLVM libc++ statische Bibliothek (c++_static)**<br>**LLVM libc++ freigegebene Bibliothek (c++_shared)**<br>
Thumb-Modus | Generieren Sie Code, der für die Thumb-Mikroarchitektur ausgeführt wird. Dies gilt nur für die ARM-Architektur. | **Thumb**<br>**Arm**<br>**Disabled** (deaktiviert)<br>
