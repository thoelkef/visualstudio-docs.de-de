---
title: Entwickeln eines Legacy-Sprachdienstes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708667"
---
# <a name="develop-a-legacy-language-service"></a>Entwickeln eines älteren Sprachdienstes
Dieser Abschnitt enthält Links zu Themen, die Ihnen beim Erstellen eines älteren Sprachdienstes helfen.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren eines Sprachdienstes finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Modell eines älteren Sprachdienstes](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Stellt ein Modell eines minimalen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sprachdienstes für den Kerneditor bereit. Sie können dieses Modell als Leitfaden zum Erstellen eines eigenen Sprachdienstes verwenden.

- [Legacy-Sprachdienstschnittstellen](../../extensibility/internals/legacy-language-service-interfaces.md)

 Erläutert die Objekte, die zum Implementieren eines Sprachdienstes erforderlich sind, und stellt eine Liste zusätzlicher Objekte bereit, die Sie zum Bereitstellen von Syntaxhervorhebungen, Methodendaten und anderen Features verwenden können.

- [Abfangen älterer Sprachdienstbefehle](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Beschreibt, wie Sie einen Befehlsfilter in ihren Sprachdienst einfügen, um Befehle abzufangen, die andernfalls in der Textansicht behandelt würden.

- [Registrieren eines älteren Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Enthält Informationen zum Registrieren Ihres Sprachdienstes mithilfe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]von .

- [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)

 Beschreibt, wie ein Sprachdienst Features zur Unterstützung eines Debuggers bereitstellen kann.

- [Checkliste: Erstellen eines älteren Sprachdienstes](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Enthält schritt für Schritt Anweisungen zum Erstellen und Integrieren eines Sprachdienstes für den Kerneditor.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Syntaxfarben in einem älteren Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Erläutert, wie Syntaxhervorhebungen in Ihrem Sprachdienst implementiert werden.

- [Anweisungsabschluss in einem älteren Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Erläutert die Anweisungsvervollständigung, den Prozess, mit dem ein Sprachdienst Benutzern hilft, ein Sprachschlüsselwort oder -element zu beenden, das sie mit der Eingabe begonnen haben.

- [Parameterinfo in einem älteren Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Beschreibt, wie Methodentipps für überladene Funktionen und Methoden angezeigt werden.

- [Gewusst wie: Bereitstellen von verdeckter Textunterstützung in einem älteren Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Erläutert den Zweck eines ausgeblendeten Textbereichs und enthält Anweisungen zum Implementieren eines ausgeblendeten Textbereichs.

- [Gewusst wie: Erweiterte Umrissunterstützung in einem legacy Sprachdienst bereitstellen](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Erläutert die beiden Optionen, die die Umrissunterstützung für Ihre Sprache über die Unterstützung des *Befehls "In Definitionen reduzieren"* hinaus erweitern.
