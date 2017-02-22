---
title: "Implementieren einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services verwaltet"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementieren einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Können Klassen in verwalteten Paketframework \(MPF\) einen ältere Sprache\-Dienst implementiert, der unterstützt eine Vielzahl von Funktionen, z. B. syntaxhervorhebung, Klammern und IntelliSense\-Vervollständigung.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren eines Sprachdiensts finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## In diesem Abschnitt  
 [Ältere Sprache Service\-Übersicht](../../extensibility/internals/legacy-language-service-overview.md)  
 Eine Übersicht über die Service\-Sprachfeatures, die in MPF unterstützt werden.  
  
 [Implementieren eines Sprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Beschreibt, was eine Sprachdienst mithilfe von MPF implementieren erforderlich ist.  
  
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Beschreibt die Schritte, die erforderlich sind, so registrieren Sie einen Dienst MPF\-basierte Sprache mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Beschreibt die zwei Parser, die für alle Funktionen eines Sprachdiensts mithilfe der MPF Implementierung erforderlich sind.  
  
 [Exemplarische Vorgehensweise: Erstellen einer Legacy\-Sprachdienst](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Enthält die grundlegenden Schritte, die erforderlich sind, eine MPF\-Sprachdienst in einem VSPackage implementieren.  
  
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte \(Legacy\-Implementierung\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Veranschaulicht die Techniken zum Abrufen einer Liste der installierten Codeausschnitte.  
  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)  
 Enthält Links zu Themen mit Details, die alle Funktionen eines Sprachdiensts mithilfe von MPF implementieren durchgeführt werden müssen.