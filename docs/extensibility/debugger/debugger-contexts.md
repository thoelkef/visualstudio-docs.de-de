---
title: Debuggerkontexte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 011999929fd4cb1508bf4958629e622684f35739
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345994"
---
# <a name="debugger-contexts"></a>Debuggerkontexte
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, die Debug-Engine (DE) arbeitet gleichzeitig in mehreren unterschiedlichen Kontexten wie folgt:

- Der Codekontext, der die aktuelle Position in der Ausführung eines Programms-Stream beschreibt.

- Die Dokumentation Kontext oder die Position, die die aktuelle Position in einem Quelldokument beschreibt.

- Der Ausdruck Evaluation-Kontext, der den Kontext beschreibt, in dem den Ausdruck Auswertung stattfinden soll.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Codekontext](../../extensibility/debugger/code-context.md) Codekontext behandelt, als eine Adresse im Anweisungsstream eines Programms, in heutigen Laufzeit-Architekturen im Vergleich zu nicht traditionelle Sprachen, in dem Code nicht von Anweisungen, aber auf andere Weise dargestellt werden kann.

 [Dokumentieren Sie Position](../../extensibility/debugger/document-position.md) definiert Dokumentposition in der Visual Studio-debugging über eine Abstraktion einer Position in einer Quelldatei als für die IDE bekannt.

 [Dokumentkontext](../../extensibility/debugger/document-context.md) erläutert, welche Dokumentenkontext darstellt, in Visual Studio-debugging in Bezug auf eine Quelldatei. Außerdem wird erläutert, wie der Symbol-Handler einen Codekontext Dokumentation Kontext zugeordnet.

 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md) enthält Informationen zu einer ausdrucksauswertungskontext in Visual Studio. Beispielsweise liefert eine ausdrucksauswertungskontext einen Stapelrahmen zugeordnet den Kontext für Ihre Evaluierung von lokalen Variablen, Methodenparameter und Klassenmember.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggen Sie Konzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Konzepte für das Debuggen Architektur.

 [Debuggen von Komponenten](../../extensibility/debugger/debugger-components.md) bietet eine Übersicht über die Visual Studio-debugging-Komponenten, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.

 [Debugtasks](../../extensibility/debugger/debugging-tasks.md) enthält Links zu verschiedenen Debuggingaufgaben ausführen, z. B. Starten eines Programms und Auswerten von Ausdrücken.