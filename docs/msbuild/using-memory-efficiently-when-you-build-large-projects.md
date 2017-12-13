---
title: Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e9484e0b8771ad665f1891298ff2f6a8a1d0005e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte
Große Projekte enthalten häufig viele Unterprojekte und andere Abhängigkeiten, die während des Buildvorgangs viel Systemspeicher beanspruchen können. Wenn der verfügbare Systemspeicher verringert wird, kann sich auch die Systemleistung verschlechtern. Ältere Versionen von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekten waren speicherintern oder wurden in Version 3.5 entfernt. Die Buildergebnisse wurden jedoch für den späteren Abruf in einem Cache aufbewahrt.  
  
 In Version 4.0 wurde diese Speicherverwaltung automatisiert, weswegen Eigenschaften wie `UnloadProjectsOnCompletion` und `UseResultsCache` nun nicht mehr in Projekten verwendet werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)