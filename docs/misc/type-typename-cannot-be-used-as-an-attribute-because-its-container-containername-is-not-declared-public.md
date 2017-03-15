---
title: "Der Typ &quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da sein Container &quot;&lt;Containername&gt;&quot; nicht als &quot;Public&quot; deklariert ist | Microsoft Docs"
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
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &quot;&lt;Typname&gt;&quot; kann nicht als Attribut verwendet werden, da sein Container &quot;&lt;Containername&gt;&quot; nicht als &quot;Public&quot; deklariert ist
Die Klasse oder das Modul, in der bzw. dem dieses Attribut definiert ist, wurde nicht mithilfe des `Public`\-Modifizierers deklariert. Klassen und Module, die keinen Zugriffsmodifizierer angeben, werden standardmäßig als `Friend` deklariert.  
  
 **Fehler\-ID:** BC31517  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie den `Public`\-Modifizierer der Klasse bzw. dem Modul hinzu, in der bzw. dem dieses Attribut definiert ist.  
  
## Siehe auch  
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)