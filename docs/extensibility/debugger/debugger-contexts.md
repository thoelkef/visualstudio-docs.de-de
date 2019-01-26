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
ms.openlocfilehash: 6a9f75167f45b364757326ddb50ef93edfc37104
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004369"
---
# <a name="debugger-contexts"></a>Debuggerkontexte
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, die Debug-Engine (DE) arbeitet gleichzeitig in mehreren unterschiedlichen Kontexten wie folgt:  
  
-   Der Codekontext, der die aktuelle Position in der Ausführung eines Programms-Stream beschreibt.  
  
-   Die Dokumentation Kontext oder die Position, die die aktuelle Position in einem Quelldokument beschreibt.  
  
-   Der Ausdruck Evaluation-Kontext, der den Kontext beschreibt, in dem den Ausdruck Auswertung stattfinden soll.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Codekontext](../../extensibility/debugger/code-context.md)  
 Erläutert Codekontext als eine Adresse im Anweisungsstream eines Programms, in heutigen Laufzeit-Architekturen im Vergleich zu nicht traditionelle Sprachen, in dem Code nicht von Anweisungen, aber auf andere Weise dargestellt werden können.  
  
 [Dokumentposition](../../extensibility/debugger/document-position.md)  
 Definiert die Dokumentposition in Visual Studio-debugging über eine Abstraktion einer Position in einer Quelldatei an, wie die IDE bekannt.  
  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)  
 Erläutert, welche Dokumentenkontext darstellt, in Visual Studio-debugging in Bezug auf eine Quelldatei. Außerdem wird erläutert, wie der Symbol-Handler einen Codekontext Dokumentation Kontext zugeordnet.  
  
 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
 Enthält Informationen über eine ausdrucksauswertungskontext in Visual Studio. Beispielsweise liefert eine ausdrucksauswertungskontext einen Stapelrahmen zugeordnet den Kontext für Ihre Evaluierung von lokalen Variablen, Methodenparameter und Klassenmember.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggen-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggen von Komponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio-debugging-Komponenten an, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.  
  
 [Tasks zum Debuggen](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggen Aufgaben wie das Starten eines Programms und Auswerten von Ausdrücken.