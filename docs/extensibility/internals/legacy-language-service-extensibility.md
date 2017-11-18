---
title: "Ältere Language Service Erweiterbarkeit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: "42"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5072aef90e08d645bff2a1bb6800e409e7d2104
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-extensibility"></a>Ältere Language Service-Erweiterbarkeit
Ein Sprachdienst bietet sprachspezifische-Unterstützung für die Bearbeitung von Quellcode in der IDE an.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Möglichkeit, einen Sprachdienst zu implementieren, finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
 Dieser Abschnitt beschreibt die Struktur und die Implementierung eines Dienstes ältere Sprache.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Migrieren eines Legacysprachdiensts](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Erläutert, wie Sie einen Sprachdienst von Visual Studio 2008 auf die neueste Version zu aktualisieren.  
  
 [Grundlagen zu Legacysprachdiensten](../../extensibility/internals/legacy-language-service-essentials.md)  
 Enthält wichtige Informationen über das Dienste für Sprachen zum Integrieren von eines Programmiersprache Ihrer Wahl in Visual Studio entwickeln.  
  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Enthält Links zu Themen, mit denen Sie einen Sprachdienst erstellen können.  
  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Enthält Informationen zur Unterstützung von syntaxhervorhebung in einen Sprachdienst.  
  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Enthält Informationen dazu, wie mithilfe des managed Package Framework (MPF) einen voll ausgestattete Sprachdienst in verwaltetem Code implementiert.  
  
 [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Beschreibt, Bibliotheken und Tools, mit die Sie Strukturansichten der Symbole in der IDE durchsuchen können.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)  
 Bietet eine Übersicht über Visual Studio-Editoren.  
  
 [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Bietet Informationen und einen Link auf der Visual Studio debuggen SDK, die die Informationen, die erforderlich sind enthält, erstellen und Anpassen von Debuggerkomponenten, die zum Debuggen von Programmen verwendet.