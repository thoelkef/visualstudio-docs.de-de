---
title: Konvertieren eines anonymen Typs in ein Tupel
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335826"
---
# <a name="convert-anonymous-type-to-tuple"></a>Konvertieren eines anonymen Typs in ein Tupel

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Konvertieren eines anonymen Typs in ein Tupel.

**Hintergrund:** Sie verfügen über einen anonymen Typ, der tupelfähig ist.

**Vorteile**: [Tupel](/dotnet/csharp/tuples) helfen dabei, die Syntax einfach zu halten. Durch diese Schnellaktion kann das C#-Feature besser verwendet werden.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einem anonymen Typ.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Konvertieren eines anonymen Typs in ein Tupel](media/convert-anon-to-tuple.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

   ![Konvertieren eines anonymen Typs in ein Tupel](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
