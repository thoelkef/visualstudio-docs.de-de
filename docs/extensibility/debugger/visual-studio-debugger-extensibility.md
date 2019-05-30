---
title: Visual Studio-Debugger-Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4184ae40a91e05b1110aed8d3e9b9c9edc64a06d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321479"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio-Debugger-Erweiterbarkeit
Visual Studio enthält einen vollständig interaktive Source Code-Debugger, ein leistungsfähiges und einfach zu verwendendes Tool für das Aufspüren von Fehlern in Ihrem Programm bereitstellen. Der Debugger hat die vollständige Unterstützung von Visual Basic, c#, C/C++- und JavaScript. Allerdings können mit der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], d. h. verfügbar der [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), anderen Programmiersprachen können in den Debugger mit den gleichen umfassenden Features unterstützt werden.

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist es die debugging-Komponenten, die, für die Sprache, die gedebuggt wird wiederum sind, das allgemeine Front-End (d. h. der Benutzeroberfläche). Für neue Sprachen, unterstützen alles, was erforderlich ist, indem die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist es die erforderlichen Back-End-Komponenten, z. B. einer Debug-Engine (DE) zu erstellen. Dieser Punkt ist, wo die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ins Spiel.

 Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält eine vollständige Referenz zu allen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Elemente, die zum Erstellen einer neuen DE erforderlich sind. Darüber hinaus stehen Beispiele und Lernprogramme, die Ihnen beim Einstieg helfen.

 Ein vollständiges Beispiel eines Sprache-Projektsystems mit debugging-Unterstützung finden Sie unter den [IronPython-Beispiel](https://www.microsoft.com/download/details.aspx?id=55984).

 In den folgenden Abschnitten wird beschrieben, wie den Debugger mit Erweitern der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>In diesem Abschnitt
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) wird beschrieben, was [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen bietet und wie Sie das SDK zu installieren.

 [Erstellen eine benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) dokumentiert die benutzerdefinierten DE-Prozess, von der Vorbereitung von Ihrem Programms für ein DE zum Trennen der DE.

 [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) wird erläutert, ob Sie eine ausdrucksauswertung schreiben müssen.

 [Auswählen einer Implementierungsstrategie für die Debug-Engine](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) wird erläutert, wie Sie Ihre DE implementieren.

 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumente der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-API.

 [Beispiele für](../../extensibility/debugger/visual-studio-debugging-samples.md) enthält Links zu einem ausdrucksauswertung (Beispiel) common Language Runtime und ein Beispiel für die Debug-Engine.
