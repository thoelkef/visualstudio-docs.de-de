---
title: 'CA1057: Eine Zeichenfolge URI-Überladungen aufrufen System.Uri Überladungen | Microsoft-Dokumentation'
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
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7cb8f559e4290c27c7b241bc15daf6ff79298372
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589158"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1057: Zeichenfolge URI-Überladungen aufrufen System.Uri Überladungen](https://docs.microsoft.com/visualstudio/code-quality/ca1057-string-uri-overloads-call-system-uri-overloads).

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert methodenüberladungen, die nur durch die Ersetzung eines Zeichenfolgenparameters mit unterscheiden sich ein <xref:System.Uri?displayProperty=fullName> Parameter und die Überladung, die den Zeichenfolgenparameter akzeptiert ruft nicht die Überladung, akzeptiert die <xref:System.Uri> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Da die Überladungen nur durch die Zeichenfolge unterscheiden /<xref:System.Uri> Parameter die Zeichenfolge wird davon ausgegangen, dass einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise. Um die Vorteile der Nutzen der <xref:System.Uri> -Klasse, die zeichenfolgenüberladung sollte Aufrufen der <xref:System.Uri> überladen, mit dem Zeichenfolgenargument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Erneut implementieren die Methode, die die Zeichenfolgendarstellung des URI verwendet werden, sodass es sich um eine Instanz erstellt die <xref:System.Uri> Klasse mit dem Zeichenfolgenargument und übergibt dann die <xref:System.Uri> Objekt an die Überladung, die die <xref:System.Uri> Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Zeichenfolgenparameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine ordnungsgemäß implementierte überlädt.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



