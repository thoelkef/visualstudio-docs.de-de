---
title: Erweiterbarkeit von Legacysprachdiensten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 691592ce59d4495af3b248dde4ebfc9af1665d55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015029"
---
# <a name="legacy-language-service-extensibility"></a>Erweiterbarkeit von Legacysprachdiensten
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