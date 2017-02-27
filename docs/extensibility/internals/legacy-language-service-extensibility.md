---
title: "&#196;ltere Sprache Service-Erweiterbarkeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste"
  - "Visual Studio Sprachdienste"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# &#196;ltere Sprache Service-Erweiterbarkeit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Sprachdienst bietet sprachspezifischen Unterstützung für das Bearbeiten von Quellcode in der IDE.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren eines Sprachdiensts finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
 Dieser Abschnitt beschreibt die Struktur und die Implementierung eines Dienstes ältere Sprache.  
  
## In diesem Abschnitt  
 [Migration von Legacy\-Language\-Dienst](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Erläutert, wie einen Language\-Dienst auf die neueste Version von Visual Studio 2008 aktualisieren.  
  
 [Ältere Sprache Service – Grundlagen](../../extensibility/internals/legacy-language-service-essentials.md)  
 Enthält wichtige Informationen zur Entwicklung von Sprachdiensten, um eine Programmiersprache in Visual Studio integrieren.  
  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Enthält Links zu Themen, die Ihnen helfen, einen Sprachdienst zu erstellen.  
  
 [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Enthält Informationen zur Unterstützung von Syntax in eine Sprachdienst markieren.  
  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Enthält Informationen dazu, wie Sie die verwalteten Paketframework \(MPF\) verwenden, um eine voll funktionsfähige Sprachdienst in verwaltetem Code zu implementieren.  
  
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Beschreibt, Bibliotheken und Tools, die es ermöglichen, Strukturansichten der Symbole in der IDE zu suchen.  
  
## Verwandte Abschnitte  
 [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md)  
 Bietet eine Übersicht über Visual Studio\-Editoren.  
  
 [Language Service\-Unterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Bietet Informationen und einen Link zu Visual Studio Debugging\-SDK, enthält die Information, die zum Erstellen und Anpassen von Debuggerkomponenten, die zum Debuggen von Programmen benötigt wird.