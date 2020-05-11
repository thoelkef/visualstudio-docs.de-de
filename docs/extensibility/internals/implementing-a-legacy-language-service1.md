---
title: Implementieren eines Legacy-Sprachdienstes1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707696"
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren eines Legacysprachdiensts
Sie können Klassen im Managed Package Framework (MPF) verwenden, um einen älteren Sprachdienst zu implementieren, der eine Vielzahl von Features unterstützt, z. B. Syntaxhervorhebung, Klammerabgleich und IntelliSense-Vervollständigung.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren eines Sprachdienstes finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)

 Eine Übersicht über die Sprachdienstfeatures, die in MPF unterstützt werden.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Beschreibt, was zum Implementieren eines Sprachdienstes mithilfe von MPF erforderlich ist.

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Beschreibt die Schritte, die zum Registrieren eines MPF-basierten Sprachdienstes bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]erforderlich sind.

- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Beschreibt die beiden Parser, die erforderlich sind, um alle Features eines Sprachdienstes mithilfe der MPF zu implementieren.

- [Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Enthält die grundlegenden Schritte, die zum Implementieren eines MPF-Sprachdienstes in einem VSPackage erforderlich sind.

- [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Veranschaulicht die Techniken zum Abrufen einer Liste installierter Codeausschnitte.

- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)

 Enthält Links zu Themen, in denen detailliert beschrieben wird, was zum Implementieren aller Features eines Sprachdienstes mithilfe von MPF getan werden muss.
