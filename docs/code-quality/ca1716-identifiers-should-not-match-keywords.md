---
title: 'CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfaef87f8463c43c412c5db3c83a899fb22b4f66
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862436"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Name, der einen Namespace, einen Typ oder ein Element Schnittstellenmembers entspricht ein reserviertes Schlüsselwort in einer Programmiersprache.

## <a name="rule-description"></a>Regelbeschreibung

Bezeichner für Namespaces, Typen und virtuelle und Schnittstellenmember sollten nicht übereinstimmen, Schlüsselwörter, die von Sprachen definiert sind, die die common Language Runtime abzielen. Abhängig von der Sprache, die verwendet wird und das Schlüsselwort, können c#-Compilerfehlern und Mehrdeutigkeiten bei die Bibliothek mit erschweren.

Diese Regel überprüft für Schlüsselwörter in den folgenden Sprachen:

- Visual Basic

- C#

- C++/CLI

Groß-/Kleinschreibung Vergleich wird zum [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Schlüsselwörter und Vergleich Groß-/Kleinschreibung wird für die anderen Sprachen verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Wählen Sie einen Namen, der nicht angezeigt wird, in der Liste der Schlüsselwörter.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können eine Warnung dieser Regel unterdrücken, wenn Sie sicher sind, dass der Bezeichner nicht Benutzer der API verwechselt werden und die Bibliothek in allen verfügbaren Sprachen in .NET Framework verwendet werden kann.