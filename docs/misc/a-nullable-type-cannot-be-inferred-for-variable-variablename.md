---
title: "F&#252;r die Variable &quot;&lt;Variablenname&gt;&quot; kann kein Typ abgeleitet werden, der NULL-Werte zul&#228;sst | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r die Variable &quot;&lt;Variablenname&gt;&quot; kann kein Typ abgeleitet werden, der NULL-Werte zul&#228;sst
Ein Typ, der NULL\-Werte zulässt, kann nicht von einem Referenztyp, z. B. einem Array, einer Klasse oder einem `String`, abgeleitet werden. Der Wert, von dem der Datentyp abgeleitet wird, muss ein Werttyp sein. Dieser Fehler wird im folgenden Code veranschaulicht.  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **Fehler\-ID:** BC36628  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Bezeichnung, die NULL\-Werte zulässt.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)