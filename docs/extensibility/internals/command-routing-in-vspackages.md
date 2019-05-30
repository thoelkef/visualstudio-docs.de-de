---
title: Befehls-Routing in VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a534a015f57a738ca65895002a6fec4454f0ae97
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342225"
---
# <a name="command-routing-in-vspackages"></a>Befehlsrouting in VSPackages
Ein Befehl ist im weitergeleitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basierend auf dem Kontext, in dem er ausgeführt wird. Es wird auf den globalen Kontext aus dem ersten Kontext nach außen weitergeleitet.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Algorithmus für das Befehlsrouting](../../extensibility/internals/command-routing-algorithm.md)

 Beschreibt die Reihenfolge der Befehl-routing-Auflösung.

- [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)

 Erläutert das Befehlsrouting.

- [Befehle und Menüs, die interop-Assemblys verwenden.](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Beschreibt Überlegungen zum routing zwischen verwaltetem Code und COM-Befehle

## <a name="related-sections"></a>Verwandte Abschnitte
- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)

 Erläutert das Modell für die Bestimmung des Benutzers Auswahl Kontext den Fokus auf ein Fenster an.

- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.