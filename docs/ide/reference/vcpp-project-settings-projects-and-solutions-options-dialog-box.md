---
title: "VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "Builds [Visual Studio], Protokolle"
  - "Buildprozess [C++]"
  - "Dateien [Visual Studio], erstellt mit dem C/C++-Compiler"
  - "Dateierweiterungen, erstellt mit dem C- oder C++-Compiler"
  - "cl.exe-Compiler, Dateierweiterungen"
  - "Erweiterungen, mit dem C- oder C++-Compiler erstellte Dateien"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Projekteinstellungen definieren, die für die Buildprotokollierung sowie unterstützende Dateitypen relevant sind.  
  
### So öffnen Sie das Dialogfeld  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Wählen Sie **Projekte und Projektmappen** aus, und wählen Sie dann **VC\+\+\-Projekteinstellungen** aus.  
  
## Suchpfad für die Buildanpassung  
 Gibt die Liste der Verzeichnisse mit RULES\-Dateien an, die Sie bei der Definition von Buildregeln für Projekte unterstützen.  
  
## Buildprotokollierung  
 **Ja**  
 Aktiviert die Generierung der Buildprotokolldatei.  Durch diese Option wird die Datei "BuildLog.htm" generiert, die sich im Zwischendateiverzeichnis des Projekts befindet.  Durch jedes neue Build wird die vorherige Datei "BuildLog.htm" überschrieben.  
  
 **Nein**  
 Deaktiviert die Generierung der Buildprotokolldatei.  
  
## Buildzeitgeber  
 **Ja**  
 Aktiviert die Zeitnahme für das Build.  Wenn diese Option ausgewählt ist, wird die Dauer der Builderstellung im Ausgabefenster ausgegeben.  Weitere Informationen finden Sie unter [Ausgabefenster](../../ide/reference/output-window.md).  
  
 **Nein**  
 Deaktiviert die Zeitnahme für das Build.  
  
## Auszublendende Erweiterungen  
 Gibt die Dateinamenerweiterungen der Dateien an, die nicht im **Projektmappen\-Explorer** angezeigt werden, wenn die Option **Alle Dateien anzeigen** aktiviert ist.  
  
## Einzuschließende Erweiterungen  
 Gibt die Dateinamenerweiterungen der Dateien an, die in das Projekt portiert werden können.  
  
## Maximale Anzahl gleichzeitiger C\+\+\-Kompilierungen  
 Gibt die maximale Anzahl von CPU\-Kernen an, die für parallele C\+\+\-Kompilierungen verwendet werden können.  
  
## Umgebung in Protokoll anzeigen  
 **Ja**  
 Listet Umgebungsvariablen in der Buildprotokolldatei auf.  Diese Option gibt an, dass während der Erstellung von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Projekten alle Umgebungsvariablen als Echo in die Buildprotokolldatei aufgenommen werden.  
  
 **Nein**  
 Schließt Umgebungsvariablen aus der Buildprotokolldatei aus.  
  
## Projektmappen\-Explorer\-Modus  
 **Nur Dateien im Projekt anzeigen**  
 Konfiguriert den **Projektmappen\-Explorer** so, dass nur Dateien im Projekt angezeigt werden.  
  
 **Alle Dateien anzeigen**  
 Konfiguriert den **Projektmappen\-Explorer** so, dass Dateien im Projekt und Dateien auf dem Datenträger im Projektordner angezeigt werden.  
  
## Siehe auch  
 [Erstellen von C\/C\+\+\-Programmen](/visual-cpp/build/building-c-cpp-programs)   
 [Referenz zur C\/C\+\+\-Erstellung](/visual-cpp/build/reference/c-cpp-building-reference)