---
title: "Syntaxfehler in Umwandlungsoperator; zwei durch Komma getrennte Argumente sind erforderlich. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Syntaxfehler in Umwandlungsoperator; zwei durch Komma getrennte Argumente sind erforderlich.
Ein Ausdruck verwendet die `CType`\-Konvertierungsfunktion oder das Konvertierungsschlüsselwort `DirectCast` oder `TryCast`, gibt jedoch nur ein Argument an.  
  
 Für `CType`, `DirectCast` und `TryCast` sind jeweils zwei Argumente erforderlich. Das erste ist ein zu konvertierender Ausdruck, und das zweite ist der Datentyp oder Klassentyp, zu dem die Konvertierung erfolgen soll.  
  
 **Fehler\-ID:** BC30944  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie beide Argumente als für die Konvertierung erforderlich an.  
  
-   Wenn Sie eine der spezifischen [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions), wie etwa `CString`, verwenden möchten, müssen Sie diesen Funktionsnamen anstelle von `CType` verwenden. Dann ist nur ein Argument erforderlich.  
  
## Siehe auch  
 [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)