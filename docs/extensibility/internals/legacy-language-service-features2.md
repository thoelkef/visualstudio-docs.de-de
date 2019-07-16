---
title: Legacysprache Service Features2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333504"
---
# <a name="legacy-language-service-features"></a>Legacy-Dienst-Sprachfunktionen
In den folgenden Themen sind einige der legacysprache-Service-Features, die Sie bereitstellen können.

 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren von eines Sprachdiensts zu suchen, finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Implementieren von Syntaxfarben erläutert.

- [Automatisches Formatieren in einem Legacysprachdienst](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Erläutert, wie die automatische Formatierung implementiert.

- [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Erläutert, wie die QuickInfo im IntelliSense-Parameter Info zu implementieren.

- [Anweisungsvervollständigung in einem Legacysprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Erläutert, wie zur Implementierung der Anweisungsliste für IntelliSense und membervervollständigungsliste.

- [Gliederung und ausgeblendeter Text in einem Legacysprachdienst](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Erläutert das Implementieren der Gliederung oder den ausgeblendeten Text.

- [Vorgehensweise: Bereitstellen von Unterstützung für erweiterte Gliederungen in einem Legacysprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Erläutert einige der Schritte bei der Implementierung von Debugger-Support...

## <a name="related-sections"></a>Verwandte Abschnitte