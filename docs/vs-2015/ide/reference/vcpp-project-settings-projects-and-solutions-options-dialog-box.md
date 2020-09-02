---
title: VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657865"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekteinstellungen definieren, die für die Buildprotokollierung sowie unterstützende Dateitypen relevant sind.

### <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Wählen Sie **Projekte und Projektmappen** aus, und wählen Sie dann **VC++-Projekteinstellungen** aus.

## <a name="build-customization-search-path"></a>Suchpfad für die Buildanpassung
 Gibt die Liste der Verzeichnisse mit RULES-Dateien an, die Sie bei der Definition von Buildregeln für Projekte unterstützen.

## <a name="build-logging"></a>Buildprotokollierung
 **Ja** Schaltet die Generierung der Buildprotokollierung ein. Durch diese Option wird die Datei "BuildLog.htm" generiert, die sich im Zwischendateiverzeichnis des Projekts befindet. Durch jedes neue Build wird die vorherige Datei "BuildLog.htm" überschrieben.

 **Nein** Deaktiviert die Generierung der buildprotokolllierungsdatei.

## <a name="build-timing"></a>Buildzeitgeber
 **Ja** Schaltet die Buildzeitdauer ein. Wenn diese Option ausgewählt ist, wird die Dauer der Builderstellung im Ausgabefenster ausgegeben. Weitere Informationen finden Sie unter [Ausgabefenster](../../ide/reference/output-window.md).

 **Nein** Deaktiviert die Erstellung des Zeitpunkts.

## <a name="extensions-to-hide"></a>Auszublendende Erweiterungen
 Gibt die Dateierweiterungen der Dateien an, die nicht im **Projektmappen-Explorer** angezeigt werden, wenn die Option **Alle Dateien anzeigen** aktiviert ist.

## <a name="extensions-to-include"></a>Einzuschließende Erweiterungen
 Gibt die Dateinamenerweiterungen der Dateien an, die in das Projekt portiert werden können.

## <a name="maximum-concurrent-c-compilations"></a>Maximale Anzahl gleichzeitiger C++-Kompilierungen
 Gibt die maximale Anzahl von CPU-Kernen an, die für parallele C++-Kompilierungen verwendet werden können.

## <a name="show-environment-in-log"></a>Umgebung in Protokoll anzeigen
 **Ja** Listet Umgebungsvariablen in der Buildprotokolldatei auf. Diese Option gibt an, dass während der Erstellung von [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekten alle Umgebungsvariablen als Echo in die Buildprotokolldatei aufgenommen werden.

 **Nein** Schließen Sie Umgebungsvariablen aus der Buildprotokollierung aus.

## <a name="solution-explorer-mode"></a>Projektmappen-Explorer-Modus
 **Nur Dateien im Projekt anzeigen** Konfiguriert **Projektmappen-Explorer** , dass nur Dateien im Projekt angezeigt werden.

 **Alle Dateien anzeigen** Konfiguriert **Projektmappen-Explorer** , um Dateien im Projekt und Dateien auf dem Datenträger im Projektordner anzuzeigen.

## <a name="see-also"></a>Weitere Informationen
 Aufbauen von c/ [C++-Programmen](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) [c/C++-Referenz](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
