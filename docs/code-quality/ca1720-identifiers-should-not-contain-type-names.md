---
title: "CA1720: Bezeichner dürfen keine Typnamen enthalten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5418bc8d265c32057911df2d3a15aaddacf1398e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Bezeichner dürfen keine Typnamen enthalten
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen.  
  
 - oder -   
  
 Der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Namen von Parametern und Membern dienen besser kommunizieren ihre Bedeutung als zur Beschreibung des Typs der erwartet wird, vom Entwicklungstools zur Verfügung gestellt werden. Für Namen von Elementen, wenn ein Datentypnamen verwendet werden muss, eine sprachunabhängige Name statt einer sprachspezifischen verwenden. Verwenden Sie anstelle der C#-Typ "Int" z. B. den sprachunabhängige Datentypnamen, Int32.  
  
 Jedes diskrete Token im Namen der Parameter- oder Membernamen wird mit den folgenden sprachspezifischen Datentypnamen, unter Beachtung verglichen:  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   "Uint"  
  
-   Ganze Zahl  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Ohne Vorzeichen  
  
-   Mit Vorzeichen  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 Darüber hinaus werden die Namen der Parameter auch mit den folgenden sprachunabhängige Datentypnamen, unter Beachtung verglichen:  
  
-   Objekt  
  
-   obj  
  
-   Boolesch  
  
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
  
-   PTR  
  
-   Zeiger  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 **Wenn für einen Parameter ausgelöst:**  
  
 Ersetzen Sie den Datentypbezeichner den Namen der Parameter durch ein Begriff, der seine Bedeutung besser beschreibt oder ein generischer Begriff, z. B. "Value".  
  
 **Wenn für ein Element, das ausgelöst wird:**  
  
 Ersetzen Sie den sprachspezifischen Datentypbezeichner, der Namen der Member mit einem Begriff, der besser die Bedeutung, eine sprachunabhängige Entsprechung oder ein generischer Begriff, z. B. "Value beschreibt" ein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Gelegentliche Nutzung eines basierende Namen für Parameter und der Member möglicherweise geeignet sein. Allerdings für neue Entwicklungen keine bekannten Szenarien auftreten, in dem Sie eine Warnung dieser Regel unterdrücken soll. Für Bibliotheken, die zuvor versandt wurden, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)