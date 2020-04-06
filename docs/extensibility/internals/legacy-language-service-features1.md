---
title: Legacy-Sprachdienstfunktionen1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707395"
---
# <a name="legacy-language-service-features"></a>Funktionen von Legacysprachdiensten
Ein MPF-Sprachdienst (Managed Package Framework) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kann ein oder mehrere Features unterstützen, z. B. Syntaxhervorhebung, IntelliSense und Haltepunktvalidierung. Jede Funktion kann unabhängig von den anderen implementiert werden, aber alle erfordern einen Parser und einen Scanner mit Ausnahme der Syntaxhervorhebung, die nur einen Scanner erfordert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den Sprachpaarabgleich zu unterstützen, der auch als Klammerabgleich bezeichnet wird.

- [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um das Kommentieren und Aufdecken von ausgewähltem Code zu unterstützen.

- [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um Dokumenteigenschaften zu unterstützen, die in eine Quelldatei eingebettet sind.

- [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um die Gliederung durch die Implementierung ausgeblendeter Regionen zu unterstützen.

- [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um das Neuformatieren von Code zu unterstützen.

- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um Codeausschnitte zu unterstützen, bei denen es sich um Codesegmente handelt, die eingefügt werden und bearbeitet werden können.

- [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Parameterinfo-Vorgang zum Anzeigen einer Methodensignatur zu unterstützen, während die Methode eingegeben wird.

- [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Schnellinfo-Vorgang zum Anzeigen von Informationen zu einem Bezeichner zu unterstützen.

- [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Memberabschlussvorgang zum Auswählen eines Mitglieds eines Namespace aus einer Liste zu unterstützen.

- [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense Complete Word-Vorgang zum Abschließen teilweise typisierter Wörter zu unterstützen.

- [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Beschreibt, was ein Sprachdienst tun kann, um das **Autos-Fenster** während des Debuggens zu unterstützen.

- [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Beschreibt, wie die **Navigationsleiste** über den oberen Rand der Editoransicht verwendet wird, um eine schnelle Navigation zu jedem Typ oder Element in der in dieser Ansicht angezeigten Datei bereitzustellen.

- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um die Syntaxhervorhebung von Quellcode zu unterstützen.

- [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Beschreibt, was ein Sprachdienst tun kann, um die Validierung von Haltepunkten außerhalb eines Debuggers zu unterstützen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Beschreibt den Parser und den Scanner, die zum Implementieren aller Features eines Sprachdienstes erforderlich sind, der das Verwaltete Paketframework verwendet.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Beschreibt, was zum Implementieren eines Sprachdienstes mithilfe der MPF erforderlich ist.

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Beschreibt die Schritte, die zum Registrieren eines MPF-basierten Sprachdienstes bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]erforderlich sind.

- [Using IntelliSense](../../ide/using-intellisense.md)

 Erläutert, wie IntelliSense den Zugriff auf Sprachreferenzen erleichtert.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Enthält Informationen zur Verwendung des Managed Package Frameworks (MPF) zum Implementieren eines sprachreichen Sprachdienstes in verwaltetem Code.
