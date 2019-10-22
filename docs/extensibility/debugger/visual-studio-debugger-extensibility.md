---
title: Erweiterbarkeit von Visual Studio-Debugger | Microsoft-Dokumentation
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
ms.openlocfilehash: 9f8a1c2148f25a1e97cfd1369770e056d1cb907d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568967"
---
# <a name="visual-studio-debugger-extensibility"></a>Erweiterbarkeit von Visual Studio-Debugger
Visual Studio enthält einen vollständig interaktiven Quellcode-Debugger, der ein leistungsfähiges und einfach zu verwendende Tool zum Nachverfolgen von Fehlern in Ihrem Programm bereitstellt. Der Debugger verfügt über eine umfassende Unterstützung C#für Visual Basic,C++, C/und JavaScript. Mit dem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], das im [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453)verfügbar ist, können jedoch andere Programmiersprachen im Debugger mit denselben umfangreichen Features unterstützt werden.

 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist das allgemeine Front-End (d. h. die Benutzeroberfläche) für die debuggingkomponenten, die wiederum spezifisch für die zu debuggende Sprache sind. Bei neuen Sprachen ist für die Unterstützung durch den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger lediglich die Erstellung der erforderlichen Back-End-Komponenten, z. b. Debug-Engine (de), erforderlich. An dieser Stelle kommt der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ins Spiel.

 Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält einen vollständigen Verweis auf alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Elemente, die zum Erstellen einer neuen de erforderlich sind. Außerdem finden Sie Beispiele und Lernprogramme, die Ihnen beim Einstieg helfen.

 Ein umfassendes Beispiel eines Sprachprojekt Systems mit Debugunterstützung finden Sie im [IronPython-Beispiel](https://www.microsoft.com/download/details.aspx?id=55984).

 In den folgenden Abschnitten wird beschrieben, wie der Debugger mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] erweitert wird.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Einstieg](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Beschreibt, was [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugging bietet und wie das SDK installiert wird.

 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentiert den benutzerdefinierten de-Prozess, von der Vorbereitung des Programms bis zum Trennen der de.

 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Erläutert, ob Sie eine Ausdrucks Auswertung schreiben müssen.

 [Auswählen einer Strategie](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) für die Debug-Engine-Implementierung Erläutert, wie Sie Ihre de implementieren.

 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentiert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-API.

 [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md) Enthält Links zu einem Beispiel für Common Language Runtime Ausdrucks Auswertung und eine Debug-Engine.
