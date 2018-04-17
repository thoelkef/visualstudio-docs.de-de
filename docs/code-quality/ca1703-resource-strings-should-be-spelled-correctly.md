---
title: 'CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden | Microsoft Docs'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd0fdccc9ee57223a6684b9caac191f1705c91c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel analysiert die Ressourcenzeichenfolge in Wörtern (zusammengesetzte Wörter versehen) und die Rechtschreibung in jeder Word-Token. Informationen zum Analysieren Algorithmus finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie vollständige Wörtern, die richtig geschrieben sind, oder ein benutzerdefiniertes Wörterbuch Wörter hinzu. Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Ändern Sie die Sprache des Wörterbuchs

Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet. Wenn Sie die Sprache der Rechtschreibprüfung ändern möchten, können Sie dies, damit durch Hinzufügen eines der folgenden Attribute auf Ihre *AssemblyInfo.cs* oder *AssemblyInfo.vb* Datei:

- Verwendung <xref:System.Reflection.AssemblyCultureAttribute> die Kultur angegeben werden, wenn Ihre Ressourcen in eine Satellitenassembly sind.
- Verwendung <xref:System.Resources.NeutralResourcesLanguageAttribute> an die *neutrale Kultur* Ihrer Assembly, wenn Ihre Ressourcen in derselben Assembly wie der Code befinden.

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur Englisch-basierte festlegen, wird diese Regel zur Codeanalyse im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Ordnungsgemäß verringern geschriebene Wörter die Zeitspanne, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)