---
title: C++-Strukturen im Klassen-Designer
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590683"
---
# <a name="c-structures-in-class-designer"></a>C++-Strukturen im Klassen-Designer

Der **Klassen-Designer** unterstützt C++-Strukturen, die mithilfe des Schlüsselworts `struct` deklariert werden. Beachten Sie folgendes Beispiel:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Weitere Informationen zur Verwendung des `struct`-Typs finden Sie unter [struct](/cpp/cpp/struct-cpp).

Eine C++-Strukturform in einem Klassendiagramm sieht wie eine Klassenform aus und funktioniert auch wie eine, außer, dass der Bezeichner **struct** heißt und er über gerade Ecken und nicht über abgerundete Ecken verfügt.

|Codeelement|Ansicht „Klassen-Designer“|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Struktur|

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit C++-Code](working-with-visual-cpp-code.md)
- [Klassen und Strukturen](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
