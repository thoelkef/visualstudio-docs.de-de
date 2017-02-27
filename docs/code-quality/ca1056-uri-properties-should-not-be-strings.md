---
title: "CA1056: URI-Eigenschaften d&#252;rfen keine Zeichenfolgen sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056: URI-Eigenschaften d&#252;rfen keine Zeichenfolgen sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ deklariert eine Zeichenfolgeneigenschaft, deren Name "uri", "Uri", "urn", "Urn", "url" oder "Url" enthält.  
  
## Regelbeschreibung  
 Diese Regel unterteilt den Eigenschaftennamen anhand der Pascal\-Schreibweise in Token und überprüft, ob die einzelnen Token "uri", "Uri", "urn", "Urn", "url" oder "Url" entsprechen.  Wenn eine Übereinstimmung gefunden wird, geht die Regel davon aus, dass die Eigenschaft einen Uniform Resource Identifier \(URI\) darstellt.  Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse\- und Codierungsfehler und kann zu Sicherheitsmängeln führen.  Die <xref:System.Uri?displayProperty=fullName>\-Klasse stellt diese Dienste auf sichere Weise bereit.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der Eigenschaft in einen <xref:System.Uri>\-Typ.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Eigenschaft keinen URI darstellt.  
  
## Beispiel  
 Im folgenden Beispiel wird der Typ veranschaulicht, der gegen diese Regel verstößt \(`ErrorProne`\) sowie der Typ, der dieser Regel entspricht \(`SaferWay`\).  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## Verwandte Regeln  
 [CA1054: URI\-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI\-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Übergeben Sie System.Uri\-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: URI\-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)