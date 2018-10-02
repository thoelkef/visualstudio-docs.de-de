---
title: 'CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cba04480cafc5aaed0ee31523d1a5f159cb6fe26
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590273"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2234: übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](https://docs.microsoft.com/visualstudio/code-quality/ca2234-pass-system-uri-objects-instead-of-strings).

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Aufruf wird einer Methode ausgelöst, die einen Zeichenfolgenparameter verfügt, deren Name "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" enthält. und der deklarierende Typ der Methode enthält eine entsprechende methodenüberladung, die eine <xref:System.Uri?displayProperty=fullName> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Parametername in Token basierend auf der Kamel unterteilt, und anschließend wird jedes Token überprüft, um festzustellen, ob es sich um "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" gleich. Wenn eine Übereinstimmung vorliegt, wird angenommen, dass der Parameter einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise. Wenn eine Auswahl zwischen zwei Überladungen, die unterscheiden sich nur bezüglich der Darstellung einer URI vorhanden ist, sollte der Benutzer auswählen die Überladung mit einem <xref:System.Uri> Argument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die Überladung, akzeptiert die <xref:System.Uri> Argument.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Zeichenfolgenparameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `ErrorProne`, die gegen die Regel und eine Methode, `SaferWay`, ordnungsgemäß Ruft die <xref:System.Uri> überladen.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



