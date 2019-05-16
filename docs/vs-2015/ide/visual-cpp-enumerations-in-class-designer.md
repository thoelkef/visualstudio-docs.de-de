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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b38d36c1fdc0033115f1d7a4cf18265dc1f2a3ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696367"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Visual C++-Enumerationen im Klassen-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Klassen-Designer unterstützt C++ `enum` und bewertete `enum class`-Typen. Beachten Sie folgendes Beispiel:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Visual C++-Code (Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Enumerationen](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)
