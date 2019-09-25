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
ms.openlocfilehash: 7a3f030c9c64d975d93aa2aeee90d37f765a6a63
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234047"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Namespace, eines Typs oder eines virtuellen oder Schnittstellenmembers entspricht einem reservierten Schlüsselwort in einer Programmiersprache.

Standardmäßig betrachtet diese Regel nur extern sichtbare Namespaces, Typen und Member, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Bezeichner für Namespaces, Typen und virtuelle Elemente und Schnittstellenmember sollten nicht mit Schlüsselwörtern verglichen werden, die von Sprachen definiert werden, die auf die Common Language Runtime abzielen. Abhängig von der verwendeten Sprache und dem Schlüsselwort können Compilerfehler und Mehrdeutigkeiten die Verwendung der Bibliothek erschweren.

Diese Regel überprüft Schlüsselwörter in den folgenden Sprachen:

- Visual Basic
- C#
- C++/CLI

Der Vergleich ohne Berücksichtigung der Groß-/Kleinschreibung wird für Visual Basic Schlüsselwörter verwendet, und für die anderen Sprachen wird der Groß-/Kleinschreibung

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Wählen Sie einen Namen aus, der nicht in der Liste der Schlüsselwörter angezeigt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie können eine Warnung aus dieser Regel unterdrücken, wenn Sie davon überzeugt sind, dass der Bezeichner die Benutzer der API nicht verwechselt und die Bibliothek in allen verfügbaren Sprachen in .net verwendbar ist.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).