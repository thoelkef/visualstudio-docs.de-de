---
title: "In einer Variablen, deren impliziter Typ &quot;Object&quot; ist, darf kein Modifizierer, der NULL-Werte zul&#228;sst, verwendet werden. | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In einer Variablen, deren impliziter Typ &quot;Object&quot; ist, darf kein Modifizierer, der NULL-Werte zul&#228;sst, verwendet werden.
Die Deklaration einer Variablen enthält den NULL\-Werte zulassenden Typmodifizierer \(?\), in der Deklaration ist aber kein Typ angegeben oder wird kein Typ abgeleitet, indem der deklarierten Variablen ein Wert zugewiesen wird.  
  
 **Fehler\-ID:** BC33112  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie einen Typ an, wenn Sie die NULL\-Werte zulassende Variable deklarieren. Der Typ darf nicht gleich <xref:System.Object> sein.  
  
-   Weisen Sie einen Wert zu, wenn Sie die NULL\-Werte zulassende Variable deklarieren. Der Typ der NULL\-Werte zulassenden Variablen wird aus dem zugewiesenen Wert abgeleitet. Der Typ des Werts darf nicht gleich <xref:System.Object> sein.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)