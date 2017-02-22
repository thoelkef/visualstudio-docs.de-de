---
title: "WPF MSBuild Task Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WPF MSBuild task reference [WPF MSBuild], term/definition table"
  - "build tasks [WPF MSBuild], Microsoft build engine"
  - "build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources"
  - "WPF MSBuild task reference [WPF MSBuild]"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WPF MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch den Windows Presentation Foundation \(WPF\)\-Buildprozess wird das Microsoft\-Buildmodul \(MSBuild\) mit einem zusätzlichen Satz von Buildaufgaben erweitert, darunter Aufgaben zur Kompilierung von Markup und zur Verarbeitung von Ressourcen.  
  
## In diesem Abschnitt  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klassifiziert eine Gruppe von Quellressourcen als die Ressourcen, die in eine Assembly eingebettet werden sollen.  Wenn eine Ressource nicht lokalisierbar ist, wird sie in die Hauptassembly der Anwendung eingebettet. Andernfalls wird sie in eine Satellitenassembly eingebettet.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generiert eine Assembly, wenn mindestens eine [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Seite eines Projekts auf einen Typ verweist, der lokal in diesem Projekt deklariert ist.  Die generierte Assembly wird entfernt, sobald der Buildprozess abgeschlossen ist oder wenn Fehler im Buildprozess auftreten.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Gibt das Verzeichnis der aktuellen [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)]\-Laufzeit zurück.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Konvertiert nicht lokalisierbare [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Projektdateien in ein kompiliertes Binärformat.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Führt einen weiteren Markupkompilierungsdurchlauf für [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Dateien aus, die auf Typen im gleichen Projekt verweisen.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Führt die Lokalisierungsattribute und die Kommentare aus mindestens einer [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Datei im Binärformat in einer Datei für die gesamte Assembly zusammen.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bettet mindestens eine Ressource \(JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] im Binärformat und andere Erweiterungstypen\) in eine RESOURCES\-Datei ein.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Überprüft, aktualisiert oder entfernt eindeutige Bezeichner \(UIDs\), um alle [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]\-Elemente in den [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]\-Quelldateien zu lokalisieren.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Fügt das **\<hostInBrowser \/\>**\-Element zum Anwendungsmanifest hinzu \(*projectname*.exe.manifest\), wenn ein [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]\-Projekt erstellt wird.  
  
## Siehe auch  
 [MSBuild](http://msdn.microsoft.com/de-de/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)