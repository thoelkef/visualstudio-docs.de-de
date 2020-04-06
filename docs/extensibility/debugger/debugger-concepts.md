---
title: Debuggerkonzepte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738984"
---
# <a name="debugger-concepts"></a>Debuggerkonzepte
Um auf dem Visual Studio-Debugpaket aufzubauen, müssen Sie mit den beim Entwerfen des Pakets verwendeten Architekturkonzepten vertraut sein.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debugsitzung](../../extensibility/debugger/debug-session.md) Erläutert die Rolle einer Sitzung in der Debugarchitektur.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) Definiert, was ein Server in Bezug auf die Debug-Architektur ist, sowohl in abstrakten als auch in physischen Begriffen.

 [Hafenlieferanten](../../extensibility/debugger/port-suppliers.md) Definiert, was ein Portlieferant in Bezug auf die Debug-Architektur ist.

 [Häfen](../../extensibility/debugger/ports.md) Definiert, was ein Port in Bezug auf die Debug-Architektur ist.

 [Prozesse](../../extensibility/debugger/processes.md) Definiert, was ein Prozess in Bezug auf die Debug-Architektur ist.

 [Programmknoten](../../extensibility/debugger/program-nodes.md) Definiert einen Programmknoten in Bezug auf die Debug-Architektur, einschließlich der Art und Weise, wie er sich selbst identifizieren kann und in welchen Prozess er ausgeführt wird.

 [Programme](../../extensibility/debugger/programs.md) Definiert ein Programm in Bezug auf die Debug-Architektur.

 [Threads](../../extensibility/debugger/threads.md) Definiert die Eigenschaften von Threads in Bezug auf die Debug-Architektur.

 [Stapelrahmen](../../extensibility/debugger/stack-frames.md) Definiert einen Stapelrahmen in Bezug auf die Debug-Architektur. Ein Stapelrahmen ist eine Abstraktion eines Stapels, die den Ausführungskontext eines Threads bereitstellt.

 [Module](../../extensibility/debugger/modules.md) Definiert ein Modul in Bezug auf die Debug-Architektur als physischen Codecontainer, z. B. eine ausführbare Datei oder eine DLL.

 [Haltepunkte](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definiert die drei Arten von Haltepunkten – ausstehend, gebunden und fehlerfrei – in Bezug auf die Debug-Architektur.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie das Debugmodul (DE) gleichzeitig in Code-, Dokumentations- und Ausdrucksauswertungskontexten arbeitet. Beschreibt für jeden der drei Kontexte den Standort, die Position oder die Bewertung, die für ihn relevant sind.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-Debuggingkomponenten, zu denen das Debugmodul (DE), der Ausdrucksevaluator (EE) und der Symbolhandler (SH) gehören.

 [Debug-Aufgaben](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debugaufgaben, z. B. zum Starten eines Programms und Auswerten von Ausdrücken.
