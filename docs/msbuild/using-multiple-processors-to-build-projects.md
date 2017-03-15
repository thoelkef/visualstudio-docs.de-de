---
title: "Using Multiple Processors to Build Projects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multiple processors"
  - "MSBuild, multiple processor systems"
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Using Multiple Processors to Build Projects
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild kann Systeme nutzen, die über mehrere Prozessoren oder Prozessoren mit mehreren Kernen verfügen.  Für jeden verfügbaren Prozessor wird ein separater Buildprozess erstellt.  Wenn das System zum Beispiel über vier Prozessoren verfügt, werden vier Buildprozesse erstellt.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann diese Builds gleichzeitig verarbeiten und daher die Gesamtbuildzeit verringern.  Das gleichzeitige Erstellen von Builds führt jedoch zu einigen Änderungen bei Buildprozessen.  In diesem Thema werden diese Änderungen erläutert.  
  
## Projekt\-zu\-Projekt\-Verweise  
 Wenn [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] einen Projekt\-zu\-Projekt\-Verweis \(P2P\) entdeckt, während parallele Builds zum Erstellen eines Projekts verwendet werden, wird der Verweis nur einmal erstellt.  Wenn zwei Projekte über den gleichen P2P\-Verweis verfügen, wird der Verweis nicht für jedes Projekt neu erstellt.  Stattdessen gibt das Buildmodul den gleichen P2P\-Verweis an beide Projekte zurück, die davon abhängen.  Zukünftige Anforderungen in der Sitzung für das gleiche Ziel erhalten den gleichen P2P\-Verweis.  
  
## Schleifenerkennung  
 Die Schleifenerkennung funktioniert genauso wie bei [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, mit der Ausnahme, dass [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nun Berichte über die Erkennung einer Schleife zu einem anderen Zeitpunkt oder im Build erstellen kann.  
  
## Fehler und Ausnahmen bei der parallelen Builderstellung  
 Bei der parallelen Builderstellung können Fehler und Ausnahmen zu einem anderen Zeitpunkt auftreten als bei der nicht parallelen Builderstellung; außerdem kann die Erstellung eines anderen Builds fortgesetzt werden, wenn ein Build nicht erstellt werden kann.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] beendet gleichzeitig ausgeführte Projektbuilds nicht zusammen mit einem fehlgeschlagenen Build.  Der Buildprozess anderer Projekte wird fortgesetzt, bis er erfolgreich abgeschlossen oder fehlgeschlagen ist.  Wenn jedoch <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> aktiviert wurde, wird die Erstellung von Builds nicht abgebrochen, auch wenn ein Fehler auftritt.  
  
## Visual C\+\+\-Projektdateien \(.vcproj\) und Projektmappendateien \(.sln\)  
 Sowohl [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projektdateien \(.vcproj\) als auch Projektmappendateien \(.sln\) können an [MSBuild\-Aufgabe](../msbuild/msbuild-task.md) übergeben werden.  Bei [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projekten wird VCWrapperProject aufgerufen, woraufhin das interne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt erstellt wird.  Für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projektmappen wird ein SolutionWrapperProject erstellt, woraufhin das interne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt erstellt wird.  In beiden Fällen wird das daraus resultierende Projekt auf die gleiche Weise behandelt wie jedes andere [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt.  
  
## Multiprozessausführung  
 Bei fast allen buildbezogenen Aktivitäten ist es erforderlich, dass das aktuelle Verzeichnis während des Buildprozesses gleich bleibt, um pfadbezogene Fehler zu vermeiden.  Aus diesem Grund können Projekte in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nicht auf verschiedenen Threads ausgeführt werden, da dies zur Erstellung mehrerer Verzeichnisse führen würde.  
  
 Um dieses Problem zu vermeiden und trotzdem Multiprozessorbuilds zu ermöglichen, verwendet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die "Prozessisolierung". Durch die Verwendung der Prozessisolierung kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] maximal `n`\-Prozesse erstellen, wobei `n` der Anzahl der im System verfügbaren Prozessoren entspricht.  Wenn [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zum Beispiel eine Lösung auf einem System mit zwei Prozessoren erstellt, werden nur zwei Buildprozessoren erstellt.  Diese Prozesse werden zum Erstellen aller Projekte der Lösung wiederverwendet.  
  
## Siehe auch  
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Tasks](../msbuild/msbuild-tasks.md)