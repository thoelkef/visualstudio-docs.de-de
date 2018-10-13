---
title: Erweiterbarkeit von Legacysprachdiensten | Microsoft-Dokumentation
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
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eecea2a957177c359d0ac40e15ce48b962bca14e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247571"
---
# <a name="legacy-language-service-extensibility"></a>Erweiterbarkeit von Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Sprachdienst bietet die sprachspezifische-Unterstützung zum Bearbeiten von Quellcode in der IDE.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
 Dieser Abschnitt beschreibt die Struktur und die Implementierung eines Dienstes legacysprache.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Migrieren eines Legacysprachdiensts](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Erläutert, wie einen Sprachdienst in Visual Studio 2008, auf die neueste Version zu aktualisieren.  
  
 [Grundlagen zu Legacysprachdiensten](../../extensibility/internals/legacy-language-service-essentials.md)  
 Enthält wichtige Informationen dazu, wie Sie Sprachdienste zum Integrieren von einer Programmiersprache in Visual Studio entwickeln.  
  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Enthält Links zu Themen, mit die Sie einen Sprachdienst erstellen können.  
  
 [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Stellt Informationen zur Unterstützung von syntaxhervorhebung in einem Sprachdienst bereit.  
  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Enthält Informationen dazu, wie Sie das managed Package Framework (MPF) verwenden, um einen Sprachdienst mit vollem Funktionsumfang in verwaltetem Code zu implementieren.  
  
 [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Beschreibt, Bibliotheken und Tools, mit denen Sie Strukturansichten von Symbolen in der IDE zu durchsuchen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)  
 Bietet eine Übersicht über Visual Studio-Editoren.  
  
 [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)  
 Enthält Informationen und einen Link auf die Visual Studio Debugging SDK, mit den Informationen, die erforderlich sind, erstellen und Anpassen von Debugger-Komponenten verwendet, um das Debuggen von Programmen an.

