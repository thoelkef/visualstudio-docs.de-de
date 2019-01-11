---
title: Referenz für die WPF-MSBuild-Task |Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15b307fa11c307a85a9a219b5ea2dd7fbc9c0476
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878548"
---
# <a name="wpf-msbuild-task-reference"></a>Referenz zu MSBuild-Tasks für WPF
Der Buildprozess von WPF erweitert die Microsoft-Build-Engine (MSBuild) durch einen zusätzlichen Satz an Buildtasks, einschließlich Tasks zum Kompilieren von Markup- und Prozessressourcen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klassifiziert eine Gruppe von Quellressourcen als diejenigen, die in eine Assembly eingebettet werden. Wenn eine Ressource nicht lokalisierbar ist, wird sie in die Hauptanwendungsassembly eingebettet; andernfalls wird sie in eine Satellitenassembly eingebettet.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generiert eine Assembly, wenn mindestens eine [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Seite in einem Projekt auf einen Typ verweist, der lokal in diesem Projekt deklariert ist. Die generierte Assembly wird entfernt, nachdem der Build abgeschlossen ist, oder wenn beim Buildprozess ein Fehler auftritt.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Gibt das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]-Runtime zurück  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Konvertiert nicht lokalisierte [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Projektdateien in kompiliertes Binärformat.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Führt den zweiten Markupkompilierungsschritt für [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Dateien aus, die auf Typen im selben Projekt verweisen.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Führt die Lokalisierungsattribute und -kommentare aus einer oder mehreren [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Binärformatdateien für die gesamte Assembly in einer einzelnen Datei zusammen  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bettet mindestens eine Ressource (*JPG*, *ICO*, *BMP*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] im Binärformat und andere Erweiterungstypen) in eine *RESOURCES*-Datei ein.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Überprüft, aktualisiert oder entfernt eindeutige Bezeichner (UIDs), um alle [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]-Elemente zu lokalisieren, die in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]-Quelldateien enthalten sind.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Fügt das Element **\<hostInBrowser />** dem Anwendungsmanifest (*\<Projektname>.exe.manifest*) hinzu, wenn ein [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]-Projekt erstellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild](../msbuild/msbuild.md)