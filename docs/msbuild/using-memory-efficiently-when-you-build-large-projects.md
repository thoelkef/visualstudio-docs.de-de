---
title: Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631314"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Effiziente Verwendung des Speichers beim Erstellen umfangreicher Projekte

Große Projekte enthalten häufig viele Unterprojekte und andere Abhängigkeiten, die während des Buildvorgangs viel Systemspeicher beanspruchen können. Wenn der verfügbare Systemspeicher verringert wird, kann sich auch die Systemleistung verschlechtern. Ältere Versionen von MSBuild-Projekten verblieben im Arbeitsspeicher. Version 3.5 entfernte frühere Versionen von Projekten, behielt jedoch Buildergebnisse für den späteren Abruf in einem Cache bei.

 In Version 4.0 wurde diese Speicherverwaltung automatisiert, weswegen Eigenschaften wie `UnloadProjectsOnCompletion` und `UseResultsCache` nun nicht mehr in Projekten verwendet werden müssen.

### <a name="see-also"></a>Siehe auch

- [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
