---
title: 'CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 279bcf3aecc2a637a7a36c2041ed63a72017a800
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545829"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name des eine Namespace-, Typ- oder virtuellen oder eine Übereinstimmung Schnittstellenmember ein reserviertes Schlüsselwort in einer Programmiersprache.

Diese Regel nur sucht standardmäßig an extern sichtbare Namespaces, Typen und Member, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Bezeichner für Namespaces, Typen und virtuelle und Schnittstellenmember sollten nicht übereinstimmen, Schlüsselwörter, die von Sprachen definiert sind, die die common Language Runtime abzielen. Abhängig von der Sprache, die verwendet wird und das Schlüsselwort, können c#-Compilerfehlern und Mehrdeutigkeiten bei die Bibliothek mit erschweren.

Diese Regel überprüft für Schlüsselwörter in den folgenden Sprachen:

- Visual Basic
- C#
- C++/CLI

Groß-/Kleinschreibung Vergleich wird verwendet, für die Visual Basic-Schlüsselwörter und Vergleich Groß-/Kleinschreibung wird für die anderen Sprachen verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Wählen Sie einen Namen, der nicht angezeigt wird, in der Liste der Schlüsselwörter.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können eine Warnung dieser Regel unterdrücken, wenn Sie überzeugt sind, dass der Bezeichner Benutzer der API verwechselt wird nicht und die Bibliothek in allen verfügbaren Sprachen in .NET verwendet werden kann.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1716.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).