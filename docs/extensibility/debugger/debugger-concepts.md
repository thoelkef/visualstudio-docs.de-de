---
title: Debuggerkonzepte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e3a9043215c5242246e54dc3e1eb2e85cd26c91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925892"
---
# <a name="debugger-concepts"></a>Debuggerkonzepte
Um auf das Visual Studio-Debug-Paket zu erstellen, müssen Sie mit der Architekturen, in das Entwerfen des Pakets verwendet Konzepten vertraut sein.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debugsitzung](../../extensibility/debugger/debug-session.md) erläutert die Rolle einer Sitzung in der debugging-Architektur.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) definiert, welche ein Server, die im Hinblick auf die Debuggen-Architektur, sowohl physische als auch abstrakte ausgedrückt ist.

 [Portieren von Lieferanten](../../extensibility/debugger/port-suppliers.md) definiert, welche ein portanbieters ist im Hinblick auf die Architektur zu debuggen.

 [Ports](../../extensibility/debugger/ports.md) definiert, welche ein Port ist, im Hinblick auf die Architektur zu debuggen.

 [Prozesse](../../extensibility/debugger/processes.md) definiert, welche ein Prozess ist, im Hinblick auf die Architektur zu debuggen.

 [Programmieren von Knoten](../../extensibility/debugger/program-nodes.md) definiert einen Programm-Knoten im Hinblick auf die Debuggen-Architektur, einschließlich, wie er sich selbst und der Prozess in läuft identifizieren kann.

 [Programme](../../extensibility/debugger/programs.md) definiert ein Programm im Hinblick auf die Architektur zu debuggen.

 [Threads](../../extensibility/debugger/threads.md) definiert die Merkmale des Threads im Hinblick auf die Architektur zu debuggen.

 [Stapelrahmen](../../extensibility/debugger/stack-frames.md) definiert ein Stapelrahmen entspricht im Hinblick auf die Architektur zu debuggen. Ein Stapelrahmen ist eine Abstraktion eines Stapels, der den Ausführungskontext eines Threads bereitstellt.

 [Module](../../extensibility/debugger/modules.md) definiert ein Modul, in Bezug auf die Architektur als physische Container für Code, z. B. eine ausführbare Datei oder eine DLL debuggen.

 [Haltepunkte](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) definiert die drei Typen von Haltepunkten, Ausstehend "," gebunden und Fehler – in Bezug auf die Architektur zu debuggen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) wird erläutert, wie die Debug-Engine (DE) gleichzeitig innerhalb von Code, Dokumentationen und Ausdruck Auswertung Kontexten ausgeführt wird. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.

 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md) bietet eine Übersicht über die Debuggen in Visual Studio-Komponenten, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.

 [Debugtasks](../../extensibility/debugger/debugging-tasks.md) enthält Links zu verschiedenen Debuggingaufgaben ausführen, z. B. Starten eines Programms und Auswerten von Ausdrücken.