---
title: Visual C++-Strukturen im Klassen-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a701aae6e9c504d24d149dd5941a0f9623111ce2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511090"
---
# <a name="visual-c-structures-in-class-designer"></a>Visual C++-Strukturen im Klassen-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual C++-Strukturen im Klassen-Designer](https://docs.microsoft.com/visualstudio/ide/visual-cpp-structures-in-class-designer).  
  
Der Klassen-Designer unterstützt C++-Strukturen, die mithilfe des Schlüsselworts `struct` deklariert werden. Beachten Sie folgendes Beispiel:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Weitere Informationen zur Verwendung des `struct`-Typs finden Sie unter [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).  
  
 Eine C++-Strukturform in einem Klassendiagramm sieht wie eine Klassenform aus und funktioniert auch wie eine, außer, dass der Bezeichner **struct** heißt und er über gerade Ecken und nicht über abgerundete Ecken verfügt.  
  
|Codeelement|Ansicht „Klassen-Designer“|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struktur|  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Visual C++-Code (Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klassen und Strukturen](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)



