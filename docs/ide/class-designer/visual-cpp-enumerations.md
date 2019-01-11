---
title: Visual C++-Enumerationen im Klassen-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dde9e749a58935e0b50b604897092f69f16300b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869202"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Visual C++-Enumerationen im Klassen-Designer

Der **Klassen-Designer** unterstützt `enum`-Typen von C++ und bewertete `enum class`-Typen. Beachten Sie folgendes Beispiel:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Eine C++-Enumerationsform in einem Klassendiagramm gleicht in Struktur und Funktionsweise einer Strukturform, sie trägt allerdings die Bezeichnung **Enum** oder **Enumerationsklasse**, sie ist nicht blau, sondern rosa und wird mit farbigem Rahmen an der linken und oberen Begrenzung angezeigt. Sowohl Enumerationsformen als auch Strukturformen sind eckig.

Weitere Informationen zur Verwendung des `enum`-Typs finden Sie unter [Enumerationen](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit Visual C++-Code](working-with-visual-cpp-code.md)
- [Enumerationen](/cpp/cpp/enumerations-cpp)