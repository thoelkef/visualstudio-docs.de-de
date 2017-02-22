---
title: "Using Memory Efficiently When You Build Large Projects | Microsoft Docs"
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
  - "memory use (MSBuild)"
  - "msbuild, efficient memory use building large trees"
  - "caching (MSBuild)"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Using Memory Efficiently When You Build Large Projects
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umfangreiche Projekte enthalten häufig Unterprojekte und andere Abhängigkeiten, die bei der Builderstellung sehr viel Systemspeicher beanspruchen.  Wenn der verfügbare Systemspeicher abnimmt, reduziert sich auch die Systemleistung.  In früheren Versionen von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verblieben Projekte im Arbeitsspeicher. In Version 3.5 wurden die Projekte entfernt, jedoch wurden die Buildergebnisse für den späteren Abruf zwischengespeichert.  
  
 In Version 4.0 erfolgt die Speicherverwaltung automatisch, sodass Eigenschaften wie `UnloadProjectsOnCompletion` und `UseResultsCache` in Projekten nicht verwendet werden müssen.  
  
## Siehe auch  
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)