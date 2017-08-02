---
title: "Verschiedene Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.newfile"
  - "VS.OpenWith"
  - "MiscellaneousFilesProject"
helpviewer_keywords: 
  - "Projektmappen, sonstige Dateien"
  - "Builds [Visual Studio], sonstige Dateien"
  - "Eigenständige Dateien"
  - "Projektmappen-Explorer, sonstige Dateien"
  - "Sonstige Dateien (Ordner)"
  - "Dateien [Visual Studio], außerhalb von Containern"
  - "Dateien [Visual Studio], Sonstige Dateien (Ordner)"
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Verschiedene Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mit den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Editoren können Sie unabhängig von einem Projekt oder einer Projektmappe mit Dateien arbeiten.  Wenn eine Projektmappe geöffnet ist, können Sie Dateien öffnen und ändern, ohne dass diese einer Projektmappe oder einem Projekt hinzugefügt werden müssen.  Dateien, mit denen Sie unabhängig von den Containern arbeiten möchten, werden als verschiedene Dateien bezeichnet.  Verschiedene Dateien sind kein Teil von Projektmappen oder Projekten, nicht in Builds enthalten und können nicht in eine Projektmappe in der Quellcodeverwaltung eingeschlossen werden.  
  
 Das Öffnen von Dateien unabhängig von einem Container ist aus mehreren Gründen nützlich.  Beispielsweise können Sie während der Entwicklung einer projektbasierten Projektmappe eine Datei anzeigen lassen, die für die Entwicklung der Projektmappe nicht relevant ist.  Übliche Beispiele umfassen Notizen oder Anweisungen für die Entwicklung, Datenbankschema und Codeausschnitte.  Möglicherweise möchten Sie auch eine eigenständige Datei erstellen.  
  
 ![Projektmappenprojekte](~/docs/ide/reference/media/projects_solutions_misc.gif "Projects\_Solutions\_Misc")  
  
 Im Projektmappen\-Explorer kann für die Dateien ein Ordner **Verschiedene Dateien** angezeigt werden, wenn die Optionen für den Ordner aktiviert sind.  Die Optionen können unter [Dokumente, Umgebung, Dialogfeld "Optionen"](../../ide/reference/documents-environment-options-dialog-box.md) festgelegt werden.  Nach dem Schließen einer der verschiedenen Dateien ist diese keiner bestimmter Projektmappe und keinem bestimmten Projekt zugeordnet, es sei denn, eine entsprechende Option wurde ebenfalls aktiviert.  
  
 Im Ordner **Verschiedene Dateien** werden die Dateien als Links dargestellt.  Obwohl dieser Ordner nicht Bestandteil einer Projektmappe ist, werden beim Öffnen einer Projektmappe abhängig von den Einstellungen für den Ordner einige oder alle der verschiedenen Dateien erneut geöffnet, die beim letzten Schließen der Projektmappe geöffnet waren.  
  
> [!NOTE]
>  Bei einigen Dateien, die im Ordner Verschiedene Dateien nicht angezeigt werden, handelt es sich um Dateien, die innerhalb der DIE nicht geändert werden können, z. B. ZIP\-Dateien und DOC\-Dateien.  Die IDE verfolgt keine Dateien, die nur über einen externen Editor geändert werden können.  
  
## In der IDE verfügbare Befehle  
 Die Menüs und Symbolleisten sowie die darin enthaltenen Befehle ändern sich in Abhängigkeit des Formats der geöffneten Datei.  Beispielsweise wird beim Öffnen einer Textdatei die Symbolleiste Text\-Editor angezeigt, und die zugehörigen Befehle sind verfügbar.  Wenn Sie dann eine XML\-Schemadatei öffnen, wird die Symbolleiste **XML\-Schema** angezeigt.  Beim Bearbeiten des XML\-Schemas sind die Befehle der Symbolleiste **Text\-Editor** \(bzw. die Symbolleiste selbst\) nicht verfügbar.  Das XML\-Schema ist das aktive Fenster und weist somit den aktuellen Auswahlkontext auf.  Wenn Sie zwischen einer Projektdatei und einer der verschiedenen Dateien wechseln, werden alle projektbezogenen Befehle ausgeblendet. Nur die Befehle, die sich direkt auf die verschiedene Datei beziehen, werden angezeigt.  
  
## Anzeigeoptionen für Ordner  
 Sie können die Anzeigeoptionen für den Ordner **Verschiedene Dateien** so festlegen, dass der Ordner auch dann angezeigt wird, wenn keine der verschiedenen Dateien geöffnet ist.  Die Projektmappendatei verwaltet nicht dauerhaft eine Liste von verschiedenen Dateien.  Sie verwendet ein optionales Feature, über das für jeden Benutzer eine MRU\-Liste \(Most Recently Used, Zuletzt geöffnet\) von Dateien gespeichert werden kann.  
  
## Siehe auch  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Dokumente, Umgebung, Dialogfeld "Optionen"](../../ide/reference/documents-environment-options-dialog-box.md)