---
title: Visual C++-Strukturen im Klassen-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 79b4adcfbcacc8cf342b5fc4183ae4fe27431b09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864769"
---
# <a name="visual-c-structures-in-class-designer"></a>Visual C++-Strukturen im Klassen-Designer

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

- [Arbeiten mit Visual C++-Code](working-with-visual-cpp-code.md)
- [Klassen und Strukturen](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)