---
title: Referenz für die WPF-MSBuild-Task |Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5266b5b6274eb9a39f6603598b90cd551f25caef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185470"
---
# <a name="wpf-msbuild-task-reference"></a>Referenz zu MSBuild-Aufgaben für WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der Buildprozess von WPF erweitert die Microsoft-Build-Engine (MSBuild) durch einen zusätzlichen Satz an Buildtasks, einschließlich Tasks zum Kompilieren von Markup- und Prozessressourcen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klassifiziert eine Gruppe von Quellressourcen als diejenigen, die in eine Assembly eingebettet werden. Wenn eine Ressource nicht lokalisierbar ist, wird sie in die Hauptanwendungsassembly eingebettet; andernfalls wird sie in eine Satellitenassembly eingebettet.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generiert eine Assembly, wenn mindestens eine [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Seite in einem Projekt auf einen Typ verweist, der lokal in diesem Projekt deklariert ist. Die generierte Assembly wird entfernt, nachdem der Build abgeschlossen ist, oder wenn beim Buildprozess ein Fehler auftritt.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Gibt das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)]-Runtime zurück  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Konvertiert nicht lokalisierte [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Projektdateien in kompiliertes Binärformat.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Führt den zweiten Markupkompilierungsschritt für [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Dateien aus, die auf Typen im selben Projekt verweisen.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Führt die Lokalisierungsattribute und -kommentare aus einer oder mehreren [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Binärformatdateien für die gesamte Assembly in einer einzelnen Datei zusammen  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bettet mindestens eine Ressource (JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] im Binärformat und andere Erweiterungstypen) in eine RESOURCES-Datei ein  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Überprüft, aktualisiert oder entfernt eindeutige Bezeichner (UIDs), um alle [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]-Elemente zu lokalisieren, die in den [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]-Quelldateien enthalten sind.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Fügt das Element **\<hostInBrowser >/** dem Anwendungsmanifest (*Projektname*.exe.manifest) hinzuzufügen, wenn ein [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]-Projekt erstellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)



