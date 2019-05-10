---
title: VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld "Optionen"
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3f81659930f75cda3c4ec0873837f7486e8b60
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789321"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld "Optionen"
In diesem Dialogfeld können Sie [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Build- und Projekteinstellungen definieren, die für die Protokollierung, die Leistung sowie unterstützende Dateitypen relevant sind.

### <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Wählen Sie **Projekte und Projektmappen** aus, und wählen Sie dann **VC++-Projekteinstellungen** aus.

## <a name="build-logging"></a>Buildprotokollierung
 **Ja**

  Aktiviert die Generierung der Buildprotokolldatei. Durch diese Option wird die Datei "BuildLog.htm" generiert, die sich im Zwischendateiverzeichnis des Projekts befindet. Durch jedes neue Build wird die vorherige Datei "BuildLog.htm" überschrieben.

 **No**

  Deaktiviert die Generierung der Buildprotokolldatei.

## <a name="show-environment-in-log"></a>Umgebung in Protokoll anzeigen
 **Ja**

 Listet Umgebungsvariablen in der Buildprotokolldatei auf. Diese Option gibt an, dass während der Erstellung von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekten alle Umgebungsvariablen als Echo in die Buildprotokolldatei aufgenommen werden.

 **No**

 Schließt Umgebungsvariablen aus der Buildprotokolldatei aus.

## <a name="build-timing"></a>Buildzeitgeber
 **Ja**

  Aktiviert die Zeitnahme für das Build. Wenn diese Option ausgewählt ist, wird die Dauer der Builderstellung im Ausgabefenster ausgegeben. Weitere Informationen finden Sie im [Ausgabefenster](../../ide/reference/output-window.md).

 **No**

 Deaktiviert die Zeitnahme für das Build.

## <a name="maximum-concurrent-c-compilations"></a>Maximale Anzahl gleichzeitiger C++-Kompilierungen
  Gibt die maximale Anzahl von CPU-Kernen an, die für parallele C++-Kompilierungen verwendet werden können.

## <a name="extensions-to-include"></a>Einzuschließende Erweiterungen
  Gibt die Dateinamenerweiterungen der Dateien an, die in das Projekt portiert werden können.

## <a name="extensions-to-hide"></a>Auszublendende Erweiterungen
  Gibt die Dateierweiterungen der Dateien an, die nicht im **Projektmappen-Explorer** angezeigt werden, wenn die Option **Alle Dateien anzeigen** aktiviert ist.

## <a name="build-customization-search-path"></a>Suchpfad für die Buildanpassung
  Gibt die Liste der Verzeichnisse mit RULES-Dateien an, die Sie bei der Definition von Buildregeln für Projekte unterstützen.

## <a name="solution-explorer-mode"></a>Projektmappen-Explorer-Modus
 **Nur Dateien im Projekt anzeigen**

  Konfiguriert den **Projektmappen-Explorer** so, dass nur Dateien im Projekt angezeigt werden.

 **Alle Dateien anzeigen**

  Konfiguriert den **Projektmappen-Explorer** so, dass Dateien im Projekt und Dateien auf dem Datenträger im Projektordner angezeigt werden.

## <a name="enable-project-caching"></a>Aktivieren der Projektzwischenspeicherung
**Ja**

Ermöglicht das Zwischenspeichern von Projektdaten in Visual Studio, damit die zwischengespeicherten Daten beim nächsten Öffnen des Projekts abrufen werden können und Sie sie nicht erneut aus den Projektdateien berechnen müssen. Durch zwischengespeicherte Daten kann die Projektladezeit deutlich verringert werden.

**No**

Kein Verwenden von zwischengespeicherten Projektdaten. Analysieren Sie die Projektdateien jedes Mal, wenn das Projekt geladen wird.

## <a name="see-also"></a>Siehe auch

- [Erstellen von C/C++-Programmen](/cpp/build/projects-and-build-systems-cpp)
- [Referenz zur C/C++-Erstellung](/cpp/build/reference/c-cpp-building-reference)