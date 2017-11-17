---
title: "CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 506421ab93cb54c11e1fdfb02c948e4cc8b23d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein
|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ deklariert eine Eigenschaft, deren Name "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" enthält.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel Token basierend auf der Pascal teilt den Eigenschaftennamen und überprüft, ob jedes Token "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" entspricht. Wenn eine Übereinstimmung vorhanden ist, wird die Regel davon ausgegangen, dass die Eigenschaft einen uniform Resource Identifier (URI) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri?displayProperty=fullName> Klasse stellt diese Dienste auf sichere Weise bereit.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Eigenschaft in einem <xref:System.Uri> Typ.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die Eigenschaft einen URI nicht darstellt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `ErrorProne`, die mit dieser Regel und einen Typ, verletzt `SaferWay`, die die Regel erfüllt.  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)