---
title: "CA1057: URI-&#220;berladungen vom Typ string rufen &#220;berladungen vom Typ System.Uri auf | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: URI-&#220;berladungen vom Typ string rufen &#220;berladungen vom Typ System.Uri auf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ deklariert Methodenüberladungen, die sich nur dadurch unterscheiden, dass ein Zeichenfolgenparameter durch einen <xref:System.Uri?displayProperty=fullName>\-Parameter ersetzt wird, und die Überladung, die den Zeichenfolgenparameter annimmt, ruft nicht die Überladung auf, die den <xref:System.Uri>\-Parameter annimmt.  
  
## Regelbeschreibung  
 Da die Überladungen sich nur durch den Zeichenfolge\/<xref:System.Uri>\-Parameter unterscheiden, wird für die Zeichenfolge angenommen, dass sie einen Uniform Resource Identifier \(URI\) darstellt.  Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse\- und Codierungsfehler und kann zu Sicherheitsmängeln führen.  Von der <xref:System.Uri>\-Klasse werden diese Dienste auf sichere Weise bereitgestellt.  Um die Vorteile der <xref:System.Uri>\-Klasse ausschöpfen zu können, sollte die Zeichenfolgenüberladung die <xref:System.Uri>\-Überladung mittels Zeichenfolgenargument aufrufen.  
  
## Behandeln von Verstößen  
 Implementieren Sie die Methode, die die Zeichenfolgendarstellung des URIs verwendet, erneut, sodass eine Instanz der <xref:System.Uri>\-Klasse unter Verwendung des Zeichenfolgenarguments erstellt und anschließend das <xref:System.Uri>\-Objekt an die Überladung übergeben wird, die über den <xref:System.Uri>\-Parameter verfügt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Zeichenfolgenparameter keinen URI darstellt.  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht eine korrekt implementierte Zeichenfolgenüberladung.  
  
 [!code-cs[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## Verwandte Regeln  
 [CA2234: Übergeben Sie System.Uri\-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056: URI\-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: URI\-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI\-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)