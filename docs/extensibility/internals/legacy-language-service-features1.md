---
title: "&#196;ltere Sprache Service Features1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Legacy-Dienst-Sprachfunktionen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Sprachdienst des verwalteten Paketframeworks \(MPF\) kann eine oder mehrere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Funktionen, z. B. Syntax\-Hervorhebung, IntelliSense und Validierung Haltepunkt unterstützen.  Jede implementierte Funktion kann unabhängig von den anderen sein, doch alle erfordern einen Parser und einen Scanner außer Syntax\-Hervorhebung, die nur einen Scanner erfordert.  
  
## In diesem Abschnitt  
 [Zugehörige Klammer in einer Legacy\-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, das abgleichende Sprachpaar zu unterstützen, abstützen auch den Vergleich.  
  
 [Kommentieren von Code in einer Legacy\-Sprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, und heben Sie die Auskommentierung des Kommentieren des ausgewählten Codes zu unterstützen.  
  
 [Benutzerdefinierte Dokumenteigenschaften in einer Legacy\-Sprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, Dokumenteigenschaften zu unterstützen, die in einer Quelldatei enthalten sind.  
  
 [Gliederung im ein Legacy\-Sprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, Gliederung von der Implementierung von ausgeblendeten Bereiche zu unterstützen.  
  
 [Formatieren von Code in einer Legacy\-Sprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, um die Neuformatierung von Code zu unterstützen.  
  
 [Unterstützung für Codeausschnitte in einem Legacy\-Sprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, Codeausschnitte zu unterstützen, die Codesegmente sind, die eingefügt und bearbeitet werden können.  
  
 [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Beschreibt, was erforderlich ist, IntelliSense\-Parameterinformationens den Vorgang zum Anzeigen einer Methodensignatur zu unterstützen, da die Methode typisiert ist.  
  
 [QuickInfo in einem Legacy\-Sprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, den Vorgang IntelliSense\-QuickInfo für die Anzeige von Informationen über einen Bezeichner zu unterstützen.  
  
 [Member\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, IntelliSense\-Member\-Abschluss den Vorgang zum Auswählen eines Mitglieds eines Namespaces aus einer Liste zu unterstützen.  
  
 [Word\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, um den vollständigen Word Vorgang von IntelliSense für das Abschließen von teilweise typisierten Wörtern zu unterstützen.  
  
 [Unterstützung für das Fenster "Auto" in eine Legacy\-Sprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Beschreibt, wie ein Sprachdienst ausführen kann, um das Fenster zu unterstützen **Auto** während des Debuggens.  
  
 [Unterstützung für die Navigationsleiste in einem Legacy\-Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Beschreibt, wie **Navigationsleiste** zum oberen Rand der Editoransicht verwendet, um schnelle Navigation zu einem Typ oder Member in der Datei bereitzustellen, die in dieser Ansicht. angezeigt wird.  
  
 [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Beschreibt, was erforderlich ist, Syntax\-Hervorhebung des Quellcodes zu unterstützen.  
  
 [Überprüfen die Haltepunkte in einem Legacy\-Sprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Beschreibt, wie ein Sprachdienst ausführen kann, um die Überprüfung von Haltepunkten außerhalb eines Debuggers zu unterstützen.  
  
## Verwandte Abschnitte  
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Beschreibt den Parser und der Scanner, die erforderlich sind, um alle Funktionen des Sprachdiensts zu implementieren, der das verwaltete Paketframework verwendet.  
  
 [Implementieren eines Sprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Beschreibt, was erforderlich ist, einen Sprachdienst zu implementieren, indem sie das MPF verwendet.  
  
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Beschreibt die Schritte, die erforderlich sind, um einen MPF\-basierten Sprachdienst mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu registrieren.  
  
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)  
 Erklärt, wie IntelliSense Sprachreferenzen sehr einfach zugegriffen wird.  
  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Enthält Informationen darüber, wie das verwaltete Paketframework \(MPF\) verwendet wird, um einen Vollfunktions sprachendienst in verwaltetem Code zu implementieren.