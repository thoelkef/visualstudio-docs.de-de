---
title: Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b214ff057125b2921ec853fbee004cbb7d41f9e0
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54792766"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Große Projekte enthalten häufig viele Unterprojekte und andere Abhängigkeiten, die während des Buildvorgangs viel Systemspeicher beanspruchen können. Wenn der verfügbare Systemspeicher verringert wird, kann sich auch die Systemleistung verschlechtern. Ältere Versionen von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekten waren speicherintern oder wurden in Version 3.5 entfernt. Die Buildergebnisse wurden jedoch für den späteren Abruf in einem Cache aufbewahrt.  
  
 In Version 4.0 wurde diese Speicherverwaltung automatisiert, weswegen Eigenschaften wie `UnloadProjectsOnCompletion` und `UseResultsCache` nun nicht mehr in Projekten verwendet werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
