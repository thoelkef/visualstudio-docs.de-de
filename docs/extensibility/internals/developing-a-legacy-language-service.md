---
title: "Entwickeln einer Legacy-Sprache | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "Language Services entwickeln"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Entwickeln einer Sprache
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält Links zu Themen, in denen einen ältere Sprache\-Dienst erstellen.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren eines Sprachdiensts finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## In diesem Abschnitt  
 [Modell eines Legacy\-Language\-Diensts](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Bietet ein Modell für einen Dienst minimale Sprache für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core\-Editor. Dieses Modell können als Leitfaden zum Erstellen Ihrer eigenen Sprachdiensts.  
  
 [Ältere Sprache\-Schnittstellen](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Erläutert die Objekte, die zum Implementieren eines Sprachdiensts und enthält eine Liste von Objekten, die Sie verwenden können, um syntaxhervorhebung, Methodendaten und andere Funktionen bereitzustellen.  
  
 [Abfangen von Legacy\-Dienst Sprachbefehle](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Beschreibt, wie einen Befehlsfilter Language Service in der Intercept\-Befehle einzufügen, die andernfalls in die Textansicht behandelt würden.  
  
 [Registrieren einer Legacy\-Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Enthält Informationen dazu, wie Sie mithilfe der Sprachdienst registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Language Service\-Unterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Beschreibt, wie eine Sprachdienst Funktionen zur Unterstützung von eines Debuggers bereitstellen kann.  
  
 [Prüfliste: Erstellen einer Legacy\-Sprachdienst](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Bietet eine schrittweise Anleitung zum Erstellen und integrieren einen Sprachdienst für den Core\-Editor.  
  
## Verwandte Abschnitte  
 [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Erläutert, wie syntaxhervorhebung in Ihrer Sprachdienst implementiert.  
  
 [Abschluss der Anweisung in eine Legacy\-Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Erläutert die Anweisungsvervollständigung, den Prozess, mit dem eine Sprachdienst hilft Benutzern, die abgeschlossen wird, ein Schlüsselwort oder ein Element, die sie eingeben gestartet wurden.  
  
 [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Beschreibt, wie die Methode Tipps für überladene Funktionen und Methoden.  
  
 [Gewusst wie: unterstützen ausgeblendeter Text in einem Legacy\-Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Erläutert den Zweck eines ausgeblendeten Text einer Region und Anweisungen zum Implementieren einer Region ausgeblendeten Text.  
  
 [Gewusst wie: unterstützen erweiterte Gliederung in eine Legacy\-Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Erläutert die zwei Optionen, die für Ihre Sprache unterstützen Gliederungsrand ausdehnen der *Definitionen* Befehl.