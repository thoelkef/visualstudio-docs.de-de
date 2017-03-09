---
title: "MSBuild-Grundlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild-Konzepte"
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild-Grundlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bietet ein einfaches XML-Schema, mit denen Sie steuern, wie die Buildplattform Software erstellt. Um die Komponenten im Build und wie sie erstellt werden sollen, verwenden Sie diese vier Teile von MSBuild: Eigenschaften, Elemente, Aufgaben und Ziele.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[MSBuild-Eigenschaften](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/ee3538c5-0d7d-4c18-a1d7-edf460cd1c8a/locales/en-US)|Hierin werden Eigenschaften und Eigenschaftenauflistungen eingeführt. Eigenschaften sind Schlüssel/Wert-Paare, die Sie zum Konfigurieren von Builds verwenden können.|  
|[Elemente](../msbuild/msbuild-items.md)|Hierin werden die allgemeinen Konzepte hinter dem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Dateiformat sowie das Zusammenwirken der einzelnen Teile beschrieben.|  
|[Ziele](../msbuild/msbuild-targets.md)|Es wird erläutert, wie Aufgaben in einer bestimmten Reihenfolge gruppiert werden und wie Sie es ermöglichen, dass Abschnitte des Buildprozesses über die Befehlszeile aufgerufen werden.|  
|[Aufgaben](../msbuild/msbuild-tasks.md)|Hierin wird gezeigt, wie eine Einheit von ausführbarem Code erstellt wird, die von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zum Ausführen unteilbarer Buildvorgänge verwendet werden kann.|  
|[Vergleich von Eigenschaften und Elementen](../msbuild/comparing-properties-and-items.md)|Vergleicht MSBuild-Eigenschaften und Elemente. Beide werden verwendet, um Informationen an Aufgaben übergeben, Bedingungen auszuwerten und speichern Sie die Werte, die in der gesamten Projektdatei verwiesen werden können.|  
|[MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md)|Erläutert, wie Sie einige escape-Zeichen, die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zur speziellen Verwendung in bestimmten Kontexten reserviert.|  
|[Exemplarische Vorgehensweise: Erstellen einer MSBuild-Projektdatei von Grund auf](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Hier wird veranschaulicht, wie eine Projektbasisdatei nur mit einem Texteditor inkrementell erstellt wird.|  
|[Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md)|Die Bausteine von MSBuild werden eingeführt, und veranschaulicht das Schreiben, bearbeiten und Debuggen von MSBuild-Projekten ohne die integrierte Entwicklungsumgebung (IDE) von Visual Studio schließen.|  
|[MSBuild-Referenz](../msbuild/msbuild-reference.md)|Enthält Links zu Dokumenten, die Informationen enthalten.|  
|[MSBuild](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d920ff78-3d00-482b-80a5-743ae3c8ab10/locales/en-US)|Bietet eine Übersicht über das XML-Schema für eine Projektdatei und Steuerung von Prozessen, die Software erstellt wird.|