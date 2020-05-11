---
title: Erweiterbarkeit von Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707407"
---
# <a name="legacy-language-service-extensibility"></a>Erweiterbarkeit von Legacysprachdiensten
Ein Sprachdienst bietet sprachspezifische Unterstützung für die Bearbeitung von Quellcode in der IDE.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren eines Sprachdienstes finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

 In diesem Abschnitt werden die Struktur und Implementierung eines älteren Sprachdienstes erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Migrieren eines Legacysprachdiensts](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Erläutert, wie sie einen Sprachdienst von Visual Studio 2008 auf die neueste Version aktualisieren.

- [Grundlagen zu Legacysprachdiensten](../../extensibility/internals/legacy-language-service-essentials.md)

 Enthält wichtige Informationen zum Entwickeln von Sprachdiensten zur Integration einer Programmiersprache in Visual Studio.

- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)

 Enthält Links zu Themen, mit denen Sie einen Sprachdienst erstellen können.

- [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Enthält Informationen zum Unterstützen der Syntaxhervorhebung in einem Sprachdienst.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Enthält Informationen zur Verwendung des Managed Package Frameworks (MPF) zum Implementieren eines sprachreichen Sprachdienstes in verwaltetem Code.

- [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Beschreibt Bibliotheken und Tools, mit denen Sie Baumansichten von Symbolen in der IDE durchsuchen können.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)

 Bietet einen Überblick über Visual Studio-Editoren.

- [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)

 Enthält Informationen und einen Link zum Visual Studio Debugging SDK, das die Informationen enthält, die zum Erstellen und Anpassen von Debuggerkomponenten zum Debuggen von Programmen erforderlich sind.
