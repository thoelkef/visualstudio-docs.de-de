---
title: C++-TypeDefs im Klassen-Designer
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590695"
---
# <a name="c-typedefs-in-class-designer"></a>C++-TypeDefs im Klassen-Designer

[TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)-Anweisungen erstellen eine oder mehrere Dereferenzierungsebenen zwischen einem Namen und seinem zugrundeliegenden Typ. Der **Klassen-Designer** unterstützt z.B. folgende TypeDef-Typen für C++, die mithilfe des Schlüsselworts `typedef` deklariert werden:

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

## <a name="class-and-struct-shapes"></a>Klassen- und Strukturformen

Eine C++-Typdefinition weist im **Klassen-Designer** die Form des in der TypeDef definierten Typs auf. Wenn die Quelle `typedef class` deklariert, hat die Form abgerundete Ecken und trägt die Bezeichnung **Class**. Für `typedef struct` hat die Form rechtwinklige Ecken und die Bezeichnung **Struct**.

Klassen und Strukturen können geschachtelte deklarierte TypeDefs enthalten. Im **Klassen-Designer** können Klassen- und Strukturformen nun geschachtelte TypeDef-Deklarationen als geschachtelte Formen anzeigen.

Typedef-Formen unterstützen die Befehle **Als Zuordnung anzeigen** und **Als Sammlungszuordnung anzeigen** im Kontextmenü.

### <a name="class-typedef-example"></a>Beispiel für eine Klassentypdefinition

```cpp
class B {};
typedef B MyB;
```

![TypeDef der C++-Klasse im Klassen-Designer](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Beispiel für eine Strukturtypdefinition

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![TypeDef der C++-Struktur im Klassen-Designer](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Unbenannte TypeDefs

Zwar können Sie eine TypeDef ohne Namen deklarieren, der **Klassen-Designer** verwendet aber nicht den Namen des Tags, den Sie angeben. Der **Klassen-Designer** verwendet den Namen, der von der **Klassenansicht** generiert wird. Beispielsweise ist folgende Deklaration gültig, wird aber in der **Klassenansicht** und im **Klassen-Designer** als ein Objekt namens **__unnamed** angezeigt:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> Der **Klassen-Designer** zeigt eine TypeDef nicht an, wenn deren Quelltyp ein Funktionszeiger ist.

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit C++-Code](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
