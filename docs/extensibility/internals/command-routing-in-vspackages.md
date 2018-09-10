---
title: Befehls-Routing in VSPackages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a5f884873e714c12708780a0e52f5f5574727fb
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512934"
---
# <a name="command-routing-in-vspackages"></a>Befehlsrouting in VSPackages
Ein Befehl ist im weitergeleitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basierend auf dem Kontext, in dem er ausgeführt wird. Es wird auf den globalen Kontext aus dem ersten Kontext nach außen weitergeleitet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Algorithmus für das Befehlsrouting](../../extensibility/internals/command-routing-algorithm.md)  
 Beschreibt die Reihenfolge der Befehl-routing-Auflösung.  
  
 [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)  
 Erläutert das Befehlsrouting.  
  
 [Befehle und Menüs, die interop-Assemblys verwenden.](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Beschreibt Überlegungen zum routing zwischen verwaltetem Code und COM-Befehle  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)  
 Erläutert das Modell für die Bestimmung des Benutzers Auswahl Kontext den Fokus auf ein Fenster an.  
  
 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.