---
title: Debuggerkontexte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738976"
---
# <a name="debugger-contexts"></a>Debuggerkontexte
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen arbeitet das Debugmodul (DE) gleichzeitig in mehreren unterschiedlichen Kontexten wie folgt:

- Der Codekontext, der die aktuelle Position im Ausführungsstream eines Programms beschreibt.

- Der Dokumentationskontext oder die Dokumentationsposition, die die aktuelle Position in einem Quelldokument beschreibt.

- Der Ausdrucksauswertungskontext, der den Kontext beschreibt, in dem die Ausdrucksauswertung stattfindet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Codekontext](../../extensibility/debugger/code-context.md) Erläutert den Codekontext als Adresse im Anweisungsstream eines Programms in den heutigen Laufzeitarchitekturen im Vergleich zu nicht traditionellen Sprachen, in denen Code möglicherweise nicht durch Anweisungen, sondern durch andere Mittel dargestellt wird.

 [Dokumentposition](../../extensibility/debugger/document-position.md) Definiert die Dokumentposition im Visual Studio-Debugging mittels einer Abstraktion einer Position in einer Quelldatei, wie sie der IDE bekannt ist.

 [Dokumentkontext](../../extensibility/debugger/document-context.md) Erläutert, was der Dokumentkontext im Visual Studio-Debugging in Bezug auf eine Quelldatei darstellt. Erläutert außerdem, wie der Symbolhandler einen Codekontext dem Dokumentationskontext zuordnet.

 [Ausdrucksbewertungskontext](../../extensibility/debugger/expression-evaluation-context.md) Stellt Informationen zu einem Ausdrucksauswertungskontext in Visual Studio bereit. Beispielsweise stellt ein Ausdrucksauswertungskontext, der einem Stapelrahmen zugeordnet ist, den Kontext zum Auswerten lokaler Variablen, Methodenparameter und Klassenmember bereit.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debug-Konzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debug-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-Debugkomponenten, zu denen das Debugmodul (DE), der Ausdrucksevaluator (EE) und der Symbolhandler (SH) gehören.

 [Debug-Aufgaben](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debugaufgaben, z. B. zum Starten eines Programms und Auswerten von Ausdrücken.
