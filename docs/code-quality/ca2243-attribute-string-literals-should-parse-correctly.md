---
title: "CA2243: Attribute-Zeichenfolgenliterale m&#252;ssen stets richtig analysiert werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2243: Attribute-Zeichenfolgenliterale m&#252;ssen stets richtig analysiert werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Der Parameter eines Attribute\-Zeichenfolgenliterals wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert.  
  
## Regelbeschreibung  
 Da Attribute von <xref:System.Attribute?displayProperty=fullName> abgeleitet und zur Kompilierzeit verwendet werden, können nur konstante Werte an ihre Konstruktoren übergeben werden.  Attributparameter zur Darstellung von URLs, GUIDs und Versionen dürfen nicht als <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> und <xref:System.Version?displayProperty=fullName> typisiert werden, da diese Typen nicht als Konstanten dargestellt werden können.  Stattdessen müssen sie durch Zeichenfolgen dargestellt werden.  
  
 Da der Parameter als Zeichenfolge typisiert wird, ist es möglich, dass zur Kompilierzeit ein falsch formatierter Parameter übergeben wird.  
  
 Diese Regel sucht Parameter, die einen Uniform Resource Identifier \(URI\), einen Globally Unique Identifier \(GUID\) oder eine Version darstellen, anhand einer Namensheuristik und stellt sicher, dass der übergebene Wert richtig ist.  
  
## Behandeln von Verstößen  
 Ändern Sie die Parameterzeichenfolge in eine URL, GUID oder Version im richtigen Format.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Parameter keine URL, GUID oder Version darstellt.  
  
## Beispiel  
 Im folgenden Beispiel wird Code für das AssemblyFileVersionAttribute veranschaulicht, das gegen diese Regel verstößt.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 Die Regel wird durch folgende Parameter ausgelöst:  
  
-   Parameter, die 'Version' enthalten und nicht in System.Version ausgewertet werden können.  
  
-   Parameter, die 'guid' enthalten und nicht in System.Guid ausgewertet werden können.  
  
-   Parameter, die 'uri', 'urn' oder 'url' enthalten und nicht in System.Uri ausgewertet werden können.  
  
## Siehe auch  
 [CA1054: URI\-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)