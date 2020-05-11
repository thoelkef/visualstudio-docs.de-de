---
title: Konvertieren eines anonymen Typs in ein Tupel
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094274"
---
# <a name="convert-anonymous-type-to-tuple"></a>Konvertieren eines anonymen Typs in ein Tupel

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Konvertieren eines anonymen Typs in ein Tupel.

**Hintergrund:** Sie verfügen über einen anonymen Typ, der tupelfähig ist.

**Vorteile**: [Tupel](/dotnet/csharp/tuples) helfen dabei, die Syntax einfach zu halten. Durch diese Schnellaktion kann das C#-Feature besser verwendet werden.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einem anonymen Typ.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Konvertieren eines anonymen Typs in ein Tupel](media/convert-anon-to-tuple.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

   ![Konvertieren eines anonymen Typs in ein Tupel](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
