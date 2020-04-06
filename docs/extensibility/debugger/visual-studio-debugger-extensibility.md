---
title: Visual Studio Debugger-Erweiterbarkeit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712498"
---
# <a name="visual-studio-debugger-extensibility"></a>Erweiterbarkeit des Visual Studio-Debuggers
Visual Studio enthält einen vollständig interaktiven Quellcode-Debugger, der ein leistungsstarkes und benutzerfreundliches Tool zum Aufspüren von Fehlern in Ihrem Programm bereitstellt. Der Debugger bietet vollständige Unterstützung für Visual Basic, C, C/C++ und JavaScript. Mit dem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], das im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835)verfügbar ist, können jedoch andere Programmiersprachen im Debugger mit den gleichen umfangreichen Funktionen unterstützt werden.

 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist das gemeinsame Front-End (d. h. die Benutzeroberfläche) für die Debugkomponenten, die wiederum spezifisch für die zu debuggende Sprache sind. Für neue Sprachen ist für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Unterstützung durch den Debugger nur das Erstellen der erforderlichen Back-End-Komponenten, z. B. eines Debugmoduls (DE), erforderlich. Hier kommt der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Punkt ins Spiel.

 Der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält einen vollständigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verweis auf alle Elemente, die zum Erstellen einer neuen DE erforderlich sind. Darüber hinaus gibt es Beispiele und Tutorials, die Ihnen helfen, loszulegen.

 Ein vollständiges Beispiel für ein Sprachprojektsystem mit Debugunterstützung finden Sie im [IronPython-Beispiel](https://www.microsoft.com/download/details.aspx?id=55984).

 In den folgenden Abschnitten wird beschrieben, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]wie der Debugger mithilfe von erweitert wird.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Beschreibt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] was das Debuggen bietet und wie das SDK installiert wird.

 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentiert den benutzerdefinierten DE-Prozess, von der Vorbereitung des Programms für eine DE bis zum Trennen der DE.

 [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Erläutert, ob Sie einen Ausdrucksbewerter schreiben müssen.

 [Auswählen einer Debug-Engine-Implementierungsstrategie](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Erläutert, wie Sie Ihre DE implementieren.

 [Referenz](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Debugging-API.

 [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md) Enthält Links zu einem Beispiel für den Common Language Runtime-Ausdrucksauswertungsbeispiel und einem Debugmodulbeispiel.
