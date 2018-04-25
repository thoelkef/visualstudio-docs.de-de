---
title: 'CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 086f902aeb89d8ee3cc63fc21a3364cfcb480266
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen
|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Erfolgt ein Aufruf an eine Methode, die einen Zeichenfolgenparameter verfügt, dessen Name "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" enthält. Der deklarierende Typ der Methode enthält eine entsprechende methodenüberladung, verfügt ein <xref:System.Uri?displayProperty=fullName> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Parametername ist Token basierend auf der Kamel aufteilen und anschließend wird jedes Token überprüft, um festzustellen, ob es sich um "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" entspricht. Wenn eine Übereinstimmung vorhanden ist, wird davon ausgegangen, dass der Parameter einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise bereit. Es gibt eine Auswahl zwischen zwei Überladungen, die sich nur bezüglich die Darstellung eines URIs unterscheiden, der Benutzer muss wählen die Überladung mit einem <xref:System.Uri> Argument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die Überladung, akzeptiert der <xref:System.Uri> Argument.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode `ErrorProne`, die gegen die Regel und eine Methode `SaferWay`, ordnungsgemäß aufruft der <xref:System.Uri> überladen.

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)