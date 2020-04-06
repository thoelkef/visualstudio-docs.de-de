---
title: Erste Schritte mit Debugger-Erweiterbarkeit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738589"
---
# <a name="get-started-with-debugger-extensibility"></a>Erste Schritte mit der Debugger-Erweiterbarkeit
Der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält die Informationen, die Sie zum Erstellen und Anpassen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von Debuggerkomponenten benötigen, die zum Debuggen von Programmen aus der Umgebung verwendet werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Das Debuggen hat Verbesserungen hinzugefügt, die sich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aus den umfangreichen Usability-Tests ergeben, die bei früheren Debuggern durchgeführt wurden. Sie können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Debuggen verwenden, um eine mehrsprachige Anwendung schrittweise zu durchlaufen, oder Sie können die spontane Bearbeitung von Variablen implementieren, während Sie Anwendungen und mehrsprachige Lösungen debuggen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Das Debuggen wird a-process ausgeführt, wobei das zu debuggende Programm ausgeführt wird und daher weniger aufdringlich im Prozessraum der Anwendung ist. Daher ist es einfacher, Komponenten zu schreiben, die mit dem Debugger interagieren, ohne dass sich dies auf das Debugprogramm auswirkt.

 Um die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]am besten zu verwenden, sollten Sie mit den folgenden Elementen vertraut sein:

- Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE)

- Die Programmiersprache C++

- ATL KOM

## <a name="in-this-section"></a>In diesem Abschnitt
 [Roadmap zum Erweitern des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Beschreibt den Prozess der Implementierung des Debuggens in Ihrem Produkt, abhängig vom Compiler und seiner Ausgabe.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet einen Überblick [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] über die Debugkomponenten, zu denen das Debugmodul (DE), der Ausdrucksevaluator (EE) und der Symbolhandler (SH) gehören.

 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie das Debugmodul (DE) gleichzeitig in Code-, Dokumentations- und Ausdrucksauswertungskontexten arbeitet. Beschreibt für jeden der drei Kontexte den Standort, die Position oder die Bewertung, die für ihn relevant sind.

 [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debugaufgaben, z. B. zum Starten eines Programms und Auswerten von Ausdrücken.
