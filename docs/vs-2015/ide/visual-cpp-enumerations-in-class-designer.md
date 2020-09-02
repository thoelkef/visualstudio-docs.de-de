---
title: Visual C++-Enumerationen im Klassen-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651668"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Visual C++-Enumerationen im Klassen-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Klassen-Designer unterstützt C++ `enum` und bewertete `enum class`-Typen. Dies ist ein Beispiel:

```
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

 Weitere Informationen zur Verwendung des `enum`-Typs finden Sie unter [Enumerationen](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Weitere Informationen
 [Arbeiten mit Visual C++ Code](../ide/working-with-visual-cpp-code-class-designer.md) - [Enumerationen](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) (Klassen-Designer)
