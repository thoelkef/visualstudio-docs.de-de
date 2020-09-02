---
title: Visual C++-Strukturen im Klassen-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646762"
---
# <a name="visual-c-structures-in-class-designer"></a>Visual C++-Strukturen im Klassen-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Klassen-Designer unterstützt C++-Strukturen, die mithilfe des Schlüsselworts `struct` deklariert werden. Dies ist ein Beispiel:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Weitere Informationen zur Verwendung des `struct`-Typs finden Sie unter [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Eine C++-Strukturform in einem Klassendiagramm sieht wie eine Klassenform aus und funktioniert auch wie eine, außer, dass der Bezeichner **struct** heißt und er über gerade Ecken und nicht über abgerundete Ecken verfügt.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Struktur|

## <a name="see-also"></a>Weitere Informationen
 [Arbeiten mit Visual C++ Code-(Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md) [Klassen und Strukturen](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [Struktur](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
