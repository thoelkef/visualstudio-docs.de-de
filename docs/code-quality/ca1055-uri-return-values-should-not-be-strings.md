---
title: "CA1055: URI-R&#252;ckgabewerte d&#252;rfen keine Zeichenfolgen sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1055: URI-R&#252;ckgabewerte d&#252;rfen keine Zeichenfolgen sein.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name einer Methode enthält "uri", "Uri", "urn", "Urn", "url" oder "Url", und die Methode gibt eine Zeichenfolge zurück.  
  
## Regelbeschreibung  
 Diese Regel teilt den Methodennamen entsprechend der Pascal\-Schreibweise in Token auf und überprüft, ob jedes Token "uri", "Uri", "urn", "Urn", "url" oder "Url" entspricht.  Wenn es eine Übereinstimmung gibt, setzt die Regel voraus, dass die Methode einen Uniform Resource Identifier \(URI\) zurückgibt.  Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse\- und Codierungsfehler und kann zu Sicherheitsmängeln führen.  Die <xref:System.Uri?displayProperty=fullName>\-Klasse stellt diese Dienste auf sichere Weise bereit.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Rückgabetyp in einen <xref:System.Uri>.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Rückgabewert keinen URI darstellt.  
  
## Beispiel  
 Im folgenden Beispiel wird der Typ veranschaulicht, der gegen diese Regel verstößt \(`ErrorProne`\) sowie der Typ, der dieser Regel entspricht \(`SaferWay`\).  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## Verwandte Regeln  
 [CA1056: URI\-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: URI\-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: Übergeben Sie System.Uri\-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: URI\-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)