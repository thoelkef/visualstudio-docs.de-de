---
title: "Der Attributkonstruktor hat einen Parameter vom Typ &quot;&lt;Typ&gt;&quot;, der kein integraler Typ, kein Gleitkomma- oder Enumerationstyp und nicht &quot;Char&quot;, &quot;String&quot;, &quot;Boolean&quot;, System.Type oder ein eindimensionales Array dieser Typen ist. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Attributkonstruktor hat einen Parameter vom Typ &quot;&lt;Typ&gt;&quot;, der kein integraler Typ, kein Gleitkomma- oder Enumerationstyp und nicht &quot;Char&quot;, &quot;String&quot;, &quot;Boolean&quot;, System.Type oder ein eindimensionales Array dieser Typen ist.
Eine benutzerdefinierte Attributdefinition enthält einen Konstruktor, der einen ungültigen Datentyp für einen Parameter angibt. Attribute können nur bestimmte Datentypen als Parameter übernehmen, da nur diese Typen in die Metadaten für die Assembly serialisiert werden können.  
  
 **Fehler\-ID:** BC30045  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Datentyp des Parameters in `Byte`, `Short`, `Integer`, `Long`, `Single`, `Double`, `Char`, `String`, `Boolean`, `System.Type` oder in einen Enumerationstyp.  
  
## Siehe auch  
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)