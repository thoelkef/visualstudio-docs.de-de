---
title: "Referenziertes Objekt hat den Wert &quot;Nothing&quot;. | Microsoft Docs"
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
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Referenziertes Objekt hat den Wert &quot;Nothing&quot;.
Das verwendete Objekt hat den Wert `Nothing`, es wurde jedoch ein verwendbarer Wert erwartet.`Nothing` ist ein Wert, der angibt, dass ein Objekt keinen Wert hat, weil ihm entweder kein Wert oder der Wert `Nothing` zugewiesen wurde.  
  
 **Fehler\-ID:** BC30760  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie das Objekt, um sicherzustellen, dass es innerhalb des Bereichs der Prozedur deklariert wurde, in dem der Fehler aufgetreten ist.  
  
2.  Prüfen Sie, ob der Wert des Objekts festgelegt ist.  
  
    > [!NOTE]
    >  Der Wert `Nothing` ist nicht identisch mit 0 \(null\) oder einer leeren Zeichenfolge. Mit `IsNothing` können Sie überprüfen, ob ein Objekt den Wert `Nothing` enthält .  
  
## Siehe auch  
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NICHT IM BUILD: IsNothing\-Funktion](http://msdn.microsoft.com/de-de/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)