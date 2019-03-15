---
title: 'CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 97b73793d0c473727960dbde8fe32fc584ff6dd5
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869205"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Aufruf erfolgt, um eine Methode, die einen Zeichenfolgenparameter verfügt, dessen Name, "Uri", "Uri", "Urn", "Urn", "Url" oder "Url enthält" und der deklarierende Typ der Methode enthält eine entsprechende methodenüberladung, die eine <xref:System.Uri?displayProperty=fullName> Parameter.

Diese Regel nur sucht standardmäßig an extern sichtbare Methoden und Typen. Dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Ein Parametername in Token basierend auf der Kamel unterteilt, und anschließend wird jedes Token überprüft, um festzustellen, ob es sich um "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" gleich. Wenn eine Übereinstimmung vorliegt, wird angenommen, dass der Parameter einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise. Wenn eine Auswahl zwischen zwei Überladungen, die unterscheiden sich nur bezüglich der Darstellung einer URI vorhanden ist, sollte der Benutzer auswählen die Überladung mit einem <xref:System.Uri> Argument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die Überladung, akzeptiert die <xref:System.Uri> Argument.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Zeichenfolgenparameter keinen URI darstellt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca2234.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Nutzung) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, `ErrorProne`, die gegen die Regel und eine Methode, `SaferWay`, ordnungsgemäß aufruft, die <xref:System.Uri> überladen:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1057: URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: URI-Rückgabewerte sollten keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)