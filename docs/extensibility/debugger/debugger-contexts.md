---
title: Debuggerkontexte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fc77e24a1a9ca72d6f689247f0de6a9e0bf26cc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098934"
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