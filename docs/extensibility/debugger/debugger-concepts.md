---
title: Debugger-Konzepte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c157e570179da1e1f16ed5c2c12af63b95b0b61d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102680"
---
# <a name="debugger-concepts"></a>Debugger-Konzepte
Um auf das debugpaket Visual Studio zu erstellen, müssen Sie mit der Architektur, verwendeten beim Entwurf des Pakets Konzepten vertraut sein.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debugsitzung](../../extensibility/debugger/debug-session.md)  
 Erläutert die Rolle einer Sitzung in der debugging-Architektur.  
  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Definiert, welche ein Servers im Hinblick auf die Debuggen-Architektur sowohl physischen als auch abstrakt ausgedrückt wird.  
  
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)  
 Definiert, was ein Lieferant Port ist im Hinblick auf die Debuggen-Architektur.  
  
 [Ports](../../extensibility/debugger/ports.md)  
 Definiert, welche ein Port ist im Hinblick auf die Debuggen-Architektur.  
  
 [Prozesse](../../extensibility/debugger/processes.md)  
 Definiert, welche ein Prozess im Hinblick auf die Debuggen-Architektur ist.  
  
 [Programmknoten](../../extensibility/debugger/program-nodes.md)  
 Definiert einen Knoten Programm im Hinblick auf die Debuggen-Architektur, einschließlich wie selbst und der Prozess ausgeführt wird, identifiziert werden kann.  
  
 [Programme](../../extensibility/debugger/programs.md)  
 Definiert ein Programm im Hinblick auf die Debuggen-Architektur.  
  
 [Threads](../../extensibility/debugger/threads.md)  
 Definiert die Eigenschaften des Threads im Hinblick auf Debuggen-Architektur.  
  
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)  
 Definiert einen Stapelrahmen im Hinblick auf die Debuggen-Architektur. Stack-Frame ist eine Abstraktion von einem Stapel, der den Ausführungskontext eines Threads bereitstellt.  
  
 [Module](../../extensibility/debugger/modules.md)  
 Definiert ein Modul, in Bezug auf die Architektur als physischen Container von Code, z. B. eine ausführbare Datei oder DLL debuggen.  
  
 [Haltepunkte](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Definiert die drei Typen von Haltepunkten – Ausstehend "," gebundenen und Fehler – im Hinblick auf die Debuggen-Architektur.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die Debugging-Modul (DE) gleichzeitig in Code, Dokumentation und ausdruckskontexten für die Auswertung ausgeführt wird. Beschreibt, für jede der drei Kontexten, die Position, Position oder Evaluation für sie relevant.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio debuggen-Komponenten, z. B. die Debugging-Modul (DE), ausdrucksauswertung (EE) und Symbol Handler ("SH").  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debugaufgaben, z. B. ein Programm starten und Auswerten von Ausdrücken.