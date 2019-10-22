---
title: Visual C++-Typedefs im Klassen-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646747"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Visual C++-Typedefs im Klassen-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typedef-Anweisungen erstellen eine oder mehrere Dereferenzierungsebenen zwischen einem Namen und seinem zugrundeliegenden Typ. Der Klassen-Designer unterstützt C++-typedef-Typen, die mithilfe des Schlüsselworts `typedef` deklariert werden, zum Beispiel:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 Sie können diesen Typ dann zum Deklarieren einer Instanz verwenden:

 `COORD OriginPoint;`

 Zwar können Sie eine typedef ohne Namen deklarieren, der Klassen-Designer verwendet aber nicht den Namen des Tags, den Sie angeben; er verwendet den Namen, den die Klassenansicht generiert. Beispielsweise ist die folgende Deklaration gültig, sie wird aber in der Klassenansicht und im Klassen-Designer als ein Objekt mit dem Namen **__unbenannt** angezeigt:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 Weitere Informationen zur Verwendung des Typs `typedef` finden Sie unter [(NOTINBUILD)typedef-Spezifizierer](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1).

 Eine C++-typedef-Form weist die Form des in der typedef definierten Typs auf. Wenn die Quelle beispielsweise `typedef class` deklariert, hat die Form abgerundete Ecken und trägt die Bezeichnung **Class**. Für `typedef struct` hat die Form rechtwinklige Ecken und die Bezeichnung **Struct**.

 Innerhalb von Klassen und Strukturen können geschachtelte typedefs deklariert sein; daher können Formen von Klassen und Strukturen geschachtelte typedef-Deklarationen als geschachtelte Formen anzeigen.

 Typedef-Formen unterstützen die Befehle **Als Zuordnung anzeigen** und **Als Sammlungszuordnung anzeigen** im Kontextmenü.

 Es folgen einige Beispiele für typdef-Typen, die vom Klassen-Designer unterstützt werden:

 `typedef type name`

 *Name* : *Typ*

 Typedef

 Zeichnet eine Zuordnungslinie zur Verbindung mit dem Typ *name*, falls möglich.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

 Typedef

 Typedef für Funktionszeiger. Es wird keine Zuordnungslinie gezeichnet.

 Der Klassen-Designer zeigt eine typedef nicht an, wenn deren Quelltyp ein Funktionszeiger ist.

```
typedef int MyInt;
class A {
   MyInt I;
};
```

 `MyInt: int`

 Typedef

 `A`

 Klasse

 Zeichnet eine Zuordnungslinie, die von der Form des Quelltyps auf die Form des Zieltyps zeigt.

 `Class B {};`

 `typedef B MyB;`

 `B`

 Klasse

 `MyB : B`

 Typedef

 Beim Klicken mit der rechten Maustaste auf eine typedef-Form und anschließendes Klicken auf **Als Zuordnung anzeigen** werden die typedef oder Klasse und eine **Alias von**-Linie angezeigt, die die beiden Formen verbindet (ähnlich einer Zuordnungslinie).

 `typedef B MyB;`

 `typedef MyB A;`

 `MyBar : Bar`

 Typedef

 Siehe oben.

```
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

 `B`

 Klasse

 `MyB : B`

 Typedef

 `A`

 Klasse

 `MyB` ist eine geschachtelte typedef-Form.

 `#include <vector>`

 `...`

 `using namespace std;`

 `...`

 `typedef vector<int> MyIntVect;`

 `vector<T>`Klasse

 `MyIntVect : vector<int>`

 Typedef

 `class B {};`

 `typedef B MyB;`

 `class A : MyB {};`

 `MyB : B`

 Typedef

 > B

 `B`

 `A`

 Klasse

 > MyB

 Der Klassen-Designer unterstützt das Anzeigen dieser Art von Beziehung nicht über Befehle des Kontextmenüs.

 `#include <vector>`

 `Typedef MyIntVect std::vector<int>;`

 `Class MyVect : MyIntVect {};`

 `std::vector<T>`

 Klasse

 `MyIntVect : std::vector<int>`

 Typedef

 `MyVect`

 Klasse

 > MyIntVect

## <a name="see-also"></a>Siehe auch
 [Arbeiten mit Visual C++ Code (Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md) [(notinbuild) typedef-Spezifizierer](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1)
