---
title: "Übersicht über die Legacy-Language-Dienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 05805e5cf4b21f4c7d233cab7dd8421ee76f626f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-overview"></a>Übersicht über die Legacy-Language-Dienst
Ein Sprachdienst bietet Unterstützung für Editor, in dem Sie bestimmte implementieren kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Funktionen. Die Dienstklassen des Managed Package Framework (MPF) Sprachen bieten vollständige Unterstützung für häufig verwendete Funktionen und teilweise Unterstützung für andere Funktionen.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Vollständig unterstützte Funktionen in das MPF  
 Die MPF-Language-Dienstklassen unterstützen die folgenden Funktionen:  
  
-   Syntaxhervorhebung  
  
-   Gliedern  
  
-   Kommentare Codeblöcke  
  
-   Zugehörige Klammer  
  
-   Codeausschnitte  
  
-   Benutzerdefinierte Dokumenteigenschaften  
  
-   IntelliSense-Parameterinformationen  
  
-   IntelliSense-QuickInfo  
  
-   Abschluss der IntelliSense-Element  
  
-   IntelliSense-wortvervollständigung  
  
## <a name="partially-supported-features-in-the-mpf"></a>Teilweise unterstützte Funktionen in das MPF  
 Das MPF bietet nur partielle Unterstützung für die folgenden Funktionen. Dies bedeutet, dass Sie die Methoden implementieren müssen, die durch das MPF aufgerufen werden.  
  
-   Formatieren von Code. Sie geben den Code, der die neuformatierung implementiert.  
  
-   Überprüfen Haltepunkte durch Identifizieren der gültigen Code umfasst. Sie geben einen Code, der den Code Spannen identifiziert.  
  
-   Den Debugger unterstützt **"Auto"** Fenster zum Anzeigen von Variablen. Sie geben den Code, der bestimmt, was Sie im Fenster angezeigt.  
  
-   Unterstützung der **Navigationsleiste** für die schnelle Navigation zwischen Typen und Member. Implementieren und eine Hilfsklasse, die die Listen in füllt Zurückgeben der **Navigationsleiste** Kombinationsfelder.  
  
## <a name="implementation"></a>Implementierung  
 Führen Sie einige Schritte zum Implementieren der Sprachdienst selbst und die Dienst-Sprachfunktionen, die Sie für Ihre Sprache unterstützen möchten. Diese Schritte werden in den folgenden Themen erläutert:  
  
-   [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)