---
title: "CA1720: Bezeichner d&#252;rfen keine Typnamen enthalten | Microsoft Docs"
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
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1720: Bezeichner d&#252;rfen keine Typnamen enthalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen.  
  
 \- oder \-  
  
 Der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.  
  
## Regelbeschreibung  
 Parameternamen und Membernamen eignen sich besser zur Vermittlung ihrer Bedeutung als zur Beschreibung des Typs. Dieser sollte von Entwicklungstools angegeben werden.  Wenn ein Datentypname verwendet werden muss, verwenden Sie für Membernamen anstelle eines sprachspezifischen Namens einen sprachunabhängigen.  Verwenden Sie z. B. statt des C\#\-Typnamens 'int' den sprachunabhängigen Datentypnamen Int32.  
  
 Jedes diskrete Token im Namen des Parameters oder Members wird unter Ignorierung der Groß\-\/Kleinschreibung mit den folgenden sprachspezifischen Typnamen verglichen:  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Unsigned  
  
-   Signed  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 Darüber hinaus werden die Namen eines Parameters auch unter Ignorierung der Groß\-\/Kleinschreibung mit den folgenden sprachunabhängigen Datentypnamen verglichen:  
  
-   Objekt  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   Zeichenfolge  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   Zeiger  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## Behandeln von Verstößen  
 **Bei Auslösung gegen einen Parameter:**  
  
 Ersetzen Sie den Datentypbezeichner im Parameternamen mit einem Begriff, der seine Bedeutung besser beschreibt, oder einem allgemeineren Begriff, z. B. 'value'.  
  
 **Bei Auslösung gegen einen Member:**  
  
 Ersetzen Sie den sprachspezifischen Datentypbezeichner im Membernamen mit einem Begriff, der seine Bedeutung besser beschreibt, einer sprachunabhängigen Entsprechung oder einem allgemeineren Begriff, z. B. 'value'.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Gelegentlich können auch typbasierte Parameter\- und Membernamen verwendet werden.  In Zusammenhang mit Neuentwicklungen kommt es jedoch zu keinem Szenario, in dem Sie eine Warnung dieser Regel unterdrücken sollten.  Bei Bibliotheken, die zuvor versandt wurden, müssen Sie u. U. eine Warnung dieser Regel unterdrücken.  
  
## Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)