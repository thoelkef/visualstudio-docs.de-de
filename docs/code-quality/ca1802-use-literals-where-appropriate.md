---
title: 'CA1802: Nach Möglichkeit Literale verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dfa50fc6007c2313191b430e9ed5445e7fd72a88
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841564"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Nach Möglichkeit Literale verwenden.

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Feld ist deklariert `static` und `readonly` (`Shared` und `ReadOnly` in Visual Basic), und mit einem Wert, der zum Zeitpunkt der Kompilierung zu berechnendes ist initialisiert wird.

Dies ist jedoch standardmäßig diese Regel nur untersucht extern sichtbaren Feldern [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Der Wert des einem `static readonly` Feld wird zur Laufzeit berechnet, wenn der statische Konstruktor für den deklarierenden Typ aufgerufen wird. Wenn die `static readonly` Feld initialisiert wird, wenn sie deklariert wurde und ein statischer Konstruktor explizit deklariert wird, gibt der Compiler einen statischen Konstruktor zum Initialisieren des Felds.

Der Wert des einem `const` Feld wird zur Kompilierungszeit berechnet und in der Metadaten, die Leistung zur Laufzeit erhöht, wenn es mit verglichen wird eine `static readonly` Feld.

Da dem verwendeten Feld zugewiesene Wert zum Zeitpunkt der Kompilierung zu berechnendes ist, ändern Sie die Deklaration zu einem `const` Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ersetzen die `static` und `readonly` Modifizierer mit den `const` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Gefahrlos unterdrücken einer Warnung dieser Regel oder die Regel deaktivieren, wenn die Leistung nicht relevant ist.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Leistung) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, `UseReadOnly`, die gegen die Regel und einen Typ, `UseConstant`, die die Regel erfüllt.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]