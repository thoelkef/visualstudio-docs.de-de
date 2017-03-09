---
title: "Die Rate kann mit den angegebenen Argumenten nicht berechnet werden. | Microsoft Docs"
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
  - "vbrFinancial_CannotCalculateRate"
ms.assetid: 17d5c8eb-4716-4b72-977f-a640c02e630d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Rate kann mit den angegebenen Argumenten nicht berechnet werden.
Die Ratenberechnung enthält nicht die erforderlichen Argumente.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit 0 \(null\) initialisiert wird.  
  
2.  Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [Financial Summary](/dotnet/visual-basic/language-reference/keywords/financial-summary)