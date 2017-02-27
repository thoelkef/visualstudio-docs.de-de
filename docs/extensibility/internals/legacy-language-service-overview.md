---
title: "&#196;ltere Sprache Service-&#220;bersicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework], über Sprachdienste"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# &#196;ltere Sprache Service-&#220;bersicht
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Sprachdienst Editor bietet Unterstützung für bestimmte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Funktionen, die Sie implementieren können.  Der Sprachdienst Klassen von verwaltetem Paketframeworks \(MPF\), bieten vollständige Unterstützung für häufig verwendete Funktionen und partielle Unterstützung für weitere Funktionen.  
  
## Völlig unterstützte Funktionen in MPF  
 Die MPF\-Sprachendienst Klassen unterstützen die folgenden Funktionen:  
  
-   Syntax\-Hervorhebung  
  
-   Gliederung  
  
-   Kommentierende Codeblöcke  
  
-   Zuordnung von Klammern  
  
-   Codeausschnitte  
  
-   Mit benutzerdefinierten Dokumenteigenschaften  
  
-   IntelliSense\-Parameterinformationen  
  
-   IntelliSense\-QuickInfo  
  
-   IntelliSense\-Memberabschluss  
  
-   IntelliSense\-Wortabschluss  
  
## Teilweise unterstützte Funktionen in MPF  
 Das MPF bietet nur partielle Unterstützung für die folgenden Features.  Dies bedeutet, dass Sie die Methoden implementieren müssen, die vom MPF aufgerufen werden.  
  
-   Neuformatierung von Code.  Sie stellen den Code, der die Neuformatierung implementiert.  
  
-   Haltepunkte durch die Bestimmung der gültigen Code spannen überprüfen.  Sie stellen den Code, der die Code spannen identifiziert.  
  
-   Der Debugger **Auto** Fenster zum Anzeigen von Variablen unterstützen.  Sie stellen den Code bereit, der bestimmt wird, was im Fenster anzuzeigen.  
  
-   **Navigationsleiste** für schnelle Navigation zwischen Typen und Membern unterstützen.  Sie implementieren und geben eine Hilfsklasse zurück, die die Listen in den **Navigationsleiste** Kombinationsfelder füllt.  
  
## Implementierung  
 Sie müssen mehrere Schritte ausführen, um den Sprachdienst selbst und die Sprachdienst Funktionen zu implementieren, die für die Sprache, die Sie unterstützen möchten.  Diese Schritte werden in den folgenden Themen erläutert:  
  
-   [Implementieren eines Sprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Zugehörige Klammer in einer Legacy\-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Gliederung im ein Legacy\-Sprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Kommentieren von Code in einer Legacy\-Sprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Formatieren von Code in einer Legacy\-Sprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Benutzerdefinierte Dokumenteigenschaften in einer Legacy\-Sprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Unterstützung für Codeausschnitte in einem Legacy\-Sprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Unterstützung für die Navigationsleiste in einem Legacy\-Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Word\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Member\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [QuickInfo in einem Legacy\-Sprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Unterstützung für das Fenster "Auto" in eine Legacy\-Sprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Überprüfen die Haltepunkte in einem Legacy\-Sprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## Siehe auch  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Ältere Sprache Service\-Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md)