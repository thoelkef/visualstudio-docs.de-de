---
title: "CA1054: URI-Parameter d&#252;rfen keine Zeichenfolgen sein | Microsoft Docs"
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
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1054: URI-Parameter d&#252;rfen keine Zeichenfolgen sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ deklariert eine Methode mit einem Zeichenfolgenparameter, dessen Name "uri", "Uri", "urn", "Urn", "url" oder "Url" enthält. Der Typ deklariert keine entsprechende Überladung, die einen <xref:System.Uri?displayProperty=fullName>\-Parameter annimmt.  
  
## Regelbeschreibung  
 Diese Regel teilt den Parameternamen entsprechend der Kamel\-Schreibweise in Token auf und überprüft, ob jedes Token "uri", "Uri", "urn", "Urn", "url" oder "Url" entspricht.  Wenn es eine Übereinstimmung gibt, geht die Regel davon aus, dass der Parameter einen Uniform Resource Identifier \(URI\) darstellt.  Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse\- und Codierungsfehler und kann zu Sicherheitsmängeln führen.  Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, sollte eine entsprechende Überladung angegeben werden, die eine Instanz der <xref:System.Uri>\-Klasse annimmt, die diese Dienste auf sichere Weise bereitstellt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Parameter in einen <xref:System.Uri>\-Typ. Dies ist eine unterbrechende Änderung.  Sie haben auch die Möglichkeit, eine Überladung der Methode anzugeben, die einen <xref:System.Uri>\-Parameter annimmt. Dies ist eine nicht unterbrechende Änderung.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Parameter keinen URI darstellt.  
  
## Beispiel  
 Im folgenden Beispiel wird der Typ veranschaulicht, der gegen diese Regel verstößt \(`ErrorProne`\) sowie der Typ, der dieser Regel entspricht \(`SaferWay`\).  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Verwandte Regeln  
 [CA1056: URI\-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: URI\-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Übergeben Sie System.Uri\-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: URI\-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)