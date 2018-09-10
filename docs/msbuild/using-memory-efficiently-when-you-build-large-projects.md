---
title: Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99550ffd42e5a3cca919ee9dd00658c66ee0e4b0
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178981"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte
Große Projekte enthalten häufig viele Unterprojekte und andere Abhängigkeiten, die während des Buildvorgangs viel Systemspeicher beanspruchen können. Wenn der verfügbare Systemspeicher verringert wird, kann sich auch die Systemleistung verschlechtern. Ältere Versionen von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekten waren speicherintern. Version 3.5 entfernte frühere Versionen von Projekten, behielt jedoch Buildergebnisse für den späteren Abruf in einem Cache bei.  
  
 In Version 4.0 wurde diese Speicherverwaltung automatisiert, weswegen Eigenschaften wie `UnloadProjectsOnCompletion` und `UseResultsCache` nun nicht mehr in Projekten verwendet werden müssen.  
  
### <a name="see-also"></a>Siehe auch  
 [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)