---
title: "Das Argument „Zzr“ muss gr&#246;&#223;er als 0 (null) sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Argument „Zzr“ muss gr&#246;&#223;er als 0 (null) sein.
Die `NPer`\-Funktion, die als Anzahl der Zeiträume für eine Annuität basierend auf regelmäßigen, festen Zahlungen und einem festen Zinssatz `Double` zurückgibt, erfordert ein Argument, das größer als 0 \(null\) ist.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Schreibweise der Argumente im Ausdruck. Ein falsch geschriebener Variablenname kann implizit eine numerische Variable erstellen, die mit 0 \(null\) initialisiert wird.  
  
-   Überprüfen Sie vorherige Operationen für Variablen im Ausdruck, insbesondere solche, die als Argumente aus anderen Prozeduren an die Prozedur übergeben werden.  
  
## Siehe auch  
 [NICHT IM BUILD: Zzr\-Funktion](http://msdn.microsoft.com/de-de/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)