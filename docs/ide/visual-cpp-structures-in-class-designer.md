---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Klassen\-Designer unterstützt C\+\+\-Strukturen, die mit dem `struct`\-Schlüsselwort deklariert werden.  Beachten Sie folgendes Beispiel:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Weitere Informationen zur Verwendung des `struct`\-Typs finden Sie unter [struct](/visual-cpp/cpp/struct-cpp).  
  
 Eine C\+\+\-Strukturform in einem Klassendiagramm gleicht in Struktur und Funktionsweise einer Klassenform. Allerdings zeigt die Bezeichnung **Struct** an, und die Ecken sind nicht gerundet.  
  
|Codeelement|Ansicht Klassen\-Designer|  
|-----------------|-------------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struktur|  
  
## Siehe auch  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klassen und Strukturen](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)