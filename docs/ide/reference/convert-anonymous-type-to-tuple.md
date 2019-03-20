---
title: Konvertieren eines anonymen Typs in ein Tupel
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b6f5dd8e53ed2e0695370a1cdcb837609be30035
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154438"
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
