---
title: Legacysprachdienste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f5a060776126756b104b7f24c7b216ac881d1b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302704"
---
# <a name="legacy-language-service-overview"></a>Übersicht über Legacysprachdienste
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einen Sprachdienst bereitstellt, Editor-Unterstützung, die bestimmte implementiert werden kann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Funktionen. Die Managed Package Framework (MPF) Sprache Dienstklassen bieten vollständige Unterstützung für häufig verwendete Funktionen und teilweise Unterstützung für andere Funktionen.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Vollständig unterstützte Funktionen in das MPF  
 Die MPF-Language-Dienstklassen unterstützen die folgenden Funktionen:  
  
-   Syntaxhervorhebung  
  
-   Gliedern  
  
-   Kommentieren Codeblöcke  
  
-   Überprüfung des Klammergleichgewichts  
  
-   Codeausschnitte  
  
-   Benutzerdefinierte Dokumenteigenschaften  
  
-   IntelliSense-Parameterinformationen  
  
-   IntelliSense-QuickInfo  
  
-   IntelliSense-membervervollständigung  
  
-   Wortvervollständigung IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Teilweise unterstützte Funktionen in das MPF  
 Das MPF bietet nur partielle Unterstützung für die folgenden Features. Dies bedeutet, dass Sie die Methoden implementieren müssen, die durch das MPF aufgerufen werden.  
  
-   Neuformatieren von Code. Sie geben Sie den Code, der neuformatierung implementiert.  
  
-   Überprüfen von Haltepunkten durch Identifizieren der gültigen Code umfasst. Sie geben Sie den Code, der die Spannen Code identifiziert.  
  
-   Den Debugger unterstützt **"Auto"** Fenster zum Anzeigen von Variablen. Sie geben Sie den Code, der bestimmt, was Sie im Fenster angezeigt.  
  
-   Unterstützung der **Navigationsleiste** für die schnelle Navigation zwischen Typen und Member. Sie implementieren und eine Hilfsklasse, die die Listen in auffüllt Zurückgeben der **Navigationsleiste** Kombinationsfelder angezeigt.  
  
## <a name="implementation"></a>Implementierung  
 Führen Sie mehrere Schritte zum Implementieren der Sprachdienst selbst und die Dienst-Sprachfunktionen, die Sie für Ihre Sprache unterstützen möchten. Diese Schritte werden in den folgenden Themen erläutert:  
  
-   [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
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
  
-   [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)

