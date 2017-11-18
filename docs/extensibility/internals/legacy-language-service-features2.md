---
title: "Ältere Language Service Features2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c91beed050f665a73622eb929fbafc482a15a78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-features"></a>Legacy-Dienst-Sprachfunktionen
In den folgenden Themen Liste einige ältere Dienst Sprachfunktionen, die Sie bereitstellen können.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Erläutert, wie Syntaxfarben implementieren.  
  
 [Automatisches Formatieren in einem Legacysprachdienst](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)  
 Erläutert, wie die automatische Formatierung implementiert.  
  
 [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Erläutert die IntelliSense-QuickInfo Parameter implementieren.  
  
 [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Es wird erläutert, wie der Anweisungsliste für IntelliSense und der Vervollständigungsliste Member implementieren.  
  
 [Gliederung und ausgeblendeter Text in einem Legacysprachdienst](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)  
 Erläutert die Gliederung oder ausgeblendeten Text zu implementieren.  
  
 [Gewusst wie: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Erläutert einige der Schritte bei der Implementierung von Debuggerunterstützung...  
  
## <a name="related-sections"></a>Verwandte Abschnitte