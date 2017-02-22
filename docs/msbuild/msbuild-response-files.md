---
title: "MSBuild Response Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "response files, MSBuild"
  - "MSBuild, response files"
  - "MSBuild, .rsp files"
  - ".rsp files"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Response Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Antwortdateien \(Erweiterung RSP\) sind Textdateien, die MSBuild.exe\-Befehlszeilenschalter enthalten.  Jeder Schalter kann sich in einer separaten Zeile befinden, oder alle Schalter können in einer Zeile enthalten sein.  Kommentarzeilen wird ein **\#**\-Symbol vorangestellt.  Der **@**\-Schalter wird verwendet, um eine andere Antwortdatei an MSBuild.exe zu übergeben.  
  
 Die Autoantwortdatei ist eine besondere RSP\-Datei, die MSBuild.exe automatisch bei der Erstellung eines Projekts verwendet.  Diese Datei, MSBuild.rsp, muss sich im gleichen Verzeichnis wie MSBuild.exe befinden, andernfalls wird sie nicht gefunden.  Sie können diese Datei bearbeiten, um Standardbefehlszeilenschalter für MSBuild.exe anzugeben.  Wenn Sie z. B. für die Erstellung von Projekten immer dieselbe Protokollierung verwenden, können Sie den **\/logger**\-Schalter zu MSBuild.rsp hinzufügen. MSBuild.exe verwendet dann bei jeder Erstellung eines Projekts diese Protokollierung.  
  
## Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)