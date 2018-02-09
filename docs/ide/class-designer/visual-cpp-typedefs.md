---
title: Visual C++-Typedefs im Klassen-Designer | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96d7e8cee6ce024040184aca50b5f5cb6facf388
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Visual C++-Typedefs im Klassen-Designer
Typedef-Anweisungen erstellen eine oder mehrere Dereferenzierungsebenen zwischen einem Namen und seinem zugrundeliegenden Typ. Der Klassen-Designer unterstützt C++-typedef-Typen, die mithilfe des Schlüsselworts `typedef` deklariert werden, zum Beispiel:  
  
```cpp
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
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```

Weitere Informationen zur Verwendung des `typedef`-Typs finden Sie unter [Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs).

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
  
```cpp
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
  
```cpp
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

[Arbeiten mit Visual C++-Code](working-with-visual-cpp-code.md)  
[Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs)