---
title: Konvertieren eines anonymen Typs in eine Klasse
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3613f365b2510111f6854087a597df387ab1a4c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335833"
---
# <a name="convert-anonymous-type-to-class"></a>Konvertieren eines anonymen Typs in eine Klasse

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Konvertieren eines anonymen Typs in eine Klasse

**Hintergrund:** Sie verfügen über einen anonymen Typ, den Sie in einer Klasse weiterentwickeln möchten.

**Vorteile**: Anonyme Typen sind nützlich, wenn Sie sie nur lokal verwenden. Sobald Ihr Code komplexer wird, ist es von Vorteil, Typen einfach zu Klassen heraufzustufen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einem anonymen Typ.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Konvertieren eines anonymen Typs in eine Klasse](media/convert-anon-to-class.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

   ![Die Konvertierung eines anonymen Typs in eine Klasse wurde akzeptiert](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
