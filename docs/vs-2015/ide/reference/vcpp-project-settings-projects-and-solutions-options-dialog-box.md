---
title: VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b6f588a1361c9184b67e510688128f621754f82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509516"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld Optionen](https://docs.microsoft.com/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box).  
  
  
In diesem Dialogfeld können Sie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekteinstellungen definieren, die für die Buildprotokollierung sowie unterstützende Dateitypen relevant sind.  
  
### <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Wählen Sie **Projekte und Projektmappen** aus, und wählen Sie dann **VC++-Projekteinstellungen** aus.  
  
## <a name="build-customization-search-path"></a>Suchpfad für die Buildanpassung  
 Gibt die Liste der Verzeichnisse mit RULES-Dateien an, die Sie bei der Definition von Buildregeln für Projekte unterstützen.  
  
## <a name="build-logging"></a>Buildprotokollierung  
 **Ja**  
 Aktiviert die Generierung der Buildprotokolldatei. Durch diese Option wird die Datei "BuildLog.htm" generiert, die sich im Zwischendateiverzeichnis des Projekts befindet. Durch jedes neue Build wird die vorherige Datei "BuildLog.htm" überschrieben.  
  
 **No**  
 Deaktiviert die Generierung der Buildprotokolldatei.  
  
## <a name="build-timing"></a>Buildzeitgeber  
 **Ja**  
 Aktiviert die Zeitnahme für das Build. Wenn diese Option ausgewählt ist, wird die Dauer der Builderstellung im Ausgabefenster ausgegeben. Weitere Informationen finden Sie im [Ausgabefenster](../../ide/reference/output-window.md).  
  
 **No**  
 Deaktiviert die Zeitnahme für das Build.  
  
## <a name="extensions-to-hide"></a>Auszublendende Erweiterungen  
 Gibt die Dateierweiterungen der Dateien an, die nicht im **Projektmappen-Explorer** angezeigt werden, wenn die Option **Alle Dateien anzeigen** aktiviert ist.  
  
## <a name="extensions-to-include"></a>Einzuschließende Erweiterungen  
 Gibt die Dateinamenerweiterungen der Dateien an, die in das Projekt portiert werden können.  
  
## <a name="maximum-concurrent-c-compilations"></a>Maximale Anzahl gleichzeitiger C++-Kompilierungen  
 Gibt die maximale Anzahl von CPU-Kernen an, die für parallele C++-Kompilierungen verwendet werden können.  
  
## <a name="show-environment-in-log"></a>Umgebung in Protokoll anzeigen  
 **Ja**  
 Listet Umgebungsvariablen in der Buildprotokolldatei auf. Diese Option gibt an, dass während der Erstellung von [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekten alle Umgebungsvariablen als Echo in die Buildprotokolldatei aufgenommen werden.  
  
 **No**  
 Schließt Umgebungsvariablen aus der Buildprotokolldatei aus.  
  
## <a name="solution-explorer-mode"></a>Projektmappen-Explorer-Modus  
 **Nur Dateien im Projekt anzeigen**  
 Konfiguriert den **Projektmappen-Explorer** so, dass nur Dateien im Projekt angezeigt werden.  
  
 **Alle Dateien anzeigen**  
 Konfiguriert den **Projektmappen-Explorer** so, dass Dateien im Projekt und Dateien auf dem Datenträger im Projektordner angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von C/C++-Programmen](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [Referenz zur C/C++-Erstellung](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)



