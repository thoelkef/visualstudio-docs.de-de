---
title: "MSBuild Error MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1011
**Geben Sie an, welches Projekt oder welche Projektmappendatei verwendet werden soll, da dieser Ordner mehrere Projekte oder Projektmappendateien enthält.**  
  
 Wenn an der Befehlszeile keine Projektdatei angegeben wird, durchsucht [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das aktuelle Arbeitsverzeichnis nach einer Datei mit der Dateierweiterung "proj" oder "sln" und verwendet diese Datei.  Das aktuelle Arbeitsverzeichnis enthält mehrere Dateien mit der Dateierweiterung "proj" oder "sln".  
  
### So beheben Sie diesen Fehler  
  
1.  Nehmen Sie den Projektdateinamen in die Befehlszeile auf.  Anstelle von `msbuild` geben Sie beispielsweise `msbuild myapp.proj` ein.  
  
## Siehe auch  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)