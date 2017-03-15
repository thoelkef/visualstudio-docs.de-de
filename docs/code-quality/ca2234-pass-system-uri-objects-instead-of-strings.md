---
title: "CA2234: &#220;bergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen | Microsoft Docs"
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
  - "PassSystemUriObjectsInsteadOfStrings"
  - "CA2234"
helpviewer_keywords: 
  - "CA2234"
  - "PassSystemUriObjectsInsteadOfStrings"
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2234: &#220;bergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode wird aufgerufen, die einen Zeichenfolgenparameter besitzt, dessen Name "uri", "Uri", "urn", "Urn", "url" oder "Url" enthält. Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen <xref:System.Uri?displayProperty=fullName>\-Parameter verfügt.  
  
## Regelbeschreibung  
 Ein Parametername wird entsprechend der Kamel\-Schreibweise in Token aufgeteilt. Anschließend wird jedes Token daraufhin überprüft, ob es "uri", "Uri", "urn", "Urn", "url" oder "Url" entspricht.  Wenn es eine Übereinstimmung gibt, wird angenommen, dass der Parameter einen Uniform Resource Identifier \(URI\) darstellt.  Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse\- und Codierungsfehler und kann zu Sicherheitsmängeln führen.  Von der <xref:System.Uri>\-Klasse werden diese Dienste auf sichere Weise bereitgestellt.  Wenn zwischen zwei Überladungen gewählt werden kann, die sich nur hinsichtlich der Darstellung eines URI unterscheiden, sollte der Benutzer die Überladung wählen, die ein <xref:System.Uri>\-Argument annimmt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die Überladung auf, die das <xref:System.Uri>\-Argument annimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Zeichenfolgenparameter keinen URI darstellt.  
  
## Beispiel  
 Das folgende Beispiel zeigt die `ErrorProne`\-Methode, die gegen die Regel verstößt, und die `SaferWay`\-Methode, durch die die <xref:System.Uri>\-Überladung ordnungsgemäß aufgerufen wird.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-cs[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## Verwandte Regeln  
 [CA1057: URI\-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056: URI\-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: URI\-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI\-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)