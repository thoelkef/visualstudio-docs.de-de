---
title: Verwenden mehrerer Prozessoren für die Erstellung von Projekten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4af67aa3961b92b55abfdcf7a811daef284ca523
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970834"
---
# <a name="use-multiple-processors-to-build-projects"></a>Verwenden mehrerer Prozessoren für die Erstellung von Projekten
MSBuild kann Systeme nutzen, die über mehrere Prozessoren oder Prozessoren mit mehreren Kernen verfügen. Für jeden verfügbaren Prozessor wird ein separater Buildprozess erstellt. Wenn das System zum Beispiel über vier Prozessoren verfügt, werden vier Buildprozesse erstellt. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann diese Builds gleichzeitig verarbeiten und daher die Gesamtbuildzeit verringern. Das gleichzeitige Erstellen von Builds führt jedoch zu einigen Änderungen bei Buildprozessen. In diesem Thema werden diese Änderungen erläutert.

## <a name="project-to-project-references"></a>Projekt-zu-Projekt-Verweise
 Wenn [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] einen Projekt-zu-Projekt-Verweis (P2P) entdeckt, während parallele Builds zum Erstellen eines Projekts verwendet werden, wird der Verweis nur einmal erstellt. Wenn zwei Projekte über den gleichen P2P-Verweis verfügen, wird der Verweis nicht für jedes Projekt neu erstellt. Stattdessen gibt die Build-Engine den gleichen P2P-Verweis an beide Projekte zurück, die davon abhängen. Zukünftige Anforderungen in der Sitzung für das gleiche Ziel erhalten den gleichen P2P-Verweis.

## <a name="cycle-detection"></a>Schleifenerkennung
 Die Zykluserkennung funktioniert genauso wie bei [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, mit der Ausnahme, dass [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nun Berichte über die Erkennung eines Zyklus zu einem anderen Zeitpunkt oder im Build erstellen kann.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Fehler und Ausnahmen bei der parallelen Builderstellung
 Bei der parallelen Builderstellung können Fehler und Ausnahmen zu einem anderen Zeitpunkt auftreten als bei der nicht parallelen Builderstellung; außerdem kann die Erstellung eines anderen Builds fortgesetzt werden, wenn ein Build nicht erstellt werden kann. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] beendet gleichzeitig ausgeführte Projektbuilds nicht zusammen mit einem fehlgeschlagenen Build. Der Buildprozess anderer Projekte wird fortgesetzt, bis er erfolgreich abgeschlossen oder fehlgeschlagen ist. Wenn jedoch <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> aktiviert wurde, wird die Erstellung von Builds nicht abgebrochen, auch wenn ein Fehler auftritt.

## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Visual C++-Projektdateien (VCPROJ) und Projektmappendateien (SLN)
 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekt- und -Projektmappendateien (*VCPROJ* und *SLN*) können beide an die [MSBuild-Aufgabe](../msbuild/msbuild-task.md) übergeben werden. Bei [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekten wird VCWrapperProject aufgerufen, woraufhin das interne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt erstellt wird. Bei [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projektmappen wird SolutionWrapperProject und anschließend das interne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt erstellt. In beiden Fällen wird das daraus resultierende Projekt auf die gleiche Weise behandelt wie jedes andere [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt.

## <a name="multi-process-execution"></a>Multiprozessausführung
 Bei fast allen buildbezogenen Aktivitäten ist es erforderlich, dass das aktuelle Verzeichnis während des Buildprozesses gleich bleibt, um pfadbezogene Fehler zu vermeiden. Aus diesem Grund können Projekte in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nicht auf verschiedenen Threads ausgeführt werden, da dies zur Erstellung mehrerer Verzeichnisse führen würde.

 Um dieses Problem zu vermeiden und trotzdem Multiprozessorbuilds zu ermöglichen, verwendet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die "Prozessisolierung". Durch die Verwendung der Prozessisolierung kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] maximal `n`-Prozesse erstellen, wobei `n` der Anzahl der im System verfügbaren Prozessoren entspricht. Wenn [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zum Beispiel eine Lösung auf einem System mit zwei Prozessoren erstellt, werden nur zwei Buildprozessoren erstellt. Diese Prozesse werden zum Erstellen aller Projekte der Lösung wiederverwendet.

## <a name="see-also"></a>Siehe auch
- [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)