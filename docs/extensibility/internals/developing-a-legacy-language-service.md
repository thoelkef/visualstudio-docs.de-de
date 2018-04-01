---
title: Entwickeln einen Sprachdienst Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b7a88c00e980cb86764958886d737d5113dfe1fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="developing-a-legacy-language-service"></a>Entwickeln von einem Legacy-Sprachdienst
Dieser Abschnitt enthält Links zu Themen, mit denen Sie erstellen einen legacy-Sprachdienst.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Modell eines Legacysprachdiensts](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Stellt ein Modell der einen minimalen Sprachdienst für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core-Editor. Sie können dieses Modell als Leitfaden zum Erstellen eigener Sprachdienst verwenden.  
  
 [Schnittstellen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Beschreibt die Objekte, die erforderlich sind, implementieren Sie einen Sprachdienst und enthält eine Liste von Objekten, die Sie verwenden können, um syntaxhervorhebung, Methodendaten und andere Funktionen bereitzustellen.  
  
 [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Beschreibt, wie einen Befehlsfilter in der Sprachdienst Intercept Befehle eingefügt, die andernfalls Textansicht behandelt würden.  
  
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Enthält Informationen zum Registrieren Ihrer Sprachdienst mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Beschreibt, wie ein Sprachdienst Funktionen zur Unterstützung von eines Debuggers bereitstellen kann.  
  
 [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Enthält schrittweise Anleitungen zum Erstellen und integrieren einen Sprachdienst für den Core-Editor.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Erläutert, wie syntaxhervorhebung in Ihre Sprachdienst zu implementieren.  
  
 [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Erläutert die Anweisungsvervollständigung, den Prozess, mit dem ein Sprachdienst hilft Benutzern, die abgeschlossen wird, ein Schlüsselwort oder ein Element, die sie eingeben gestartet wurden.  
  
 [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Beschreibt, wie die Methode Tipps für überladene Funktionen und Methoden bereitzustellen.  
  
 [Gewusst wie: Unterstützen von ausgeblendetem Text in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Erläutert den Zweck eines Datenbereichs ausgeblendetem Text, und bietet Anweisungen zum Implementieren einer Region ausgeblendeten Text.  
  
 [Gewusst wie: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Erläutert die zwei Optionen, die für Ihre Sprache nicht nur Unterstützung für Gliederungsmodus ausdehnen der *Definitionen* Befehl.