---
title: Konvertieren eines anonymen Typs in eine Klasse
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809210"
---
# <a name="convert-anonymous-type-to-class"></a>Konvertieren eines anonymen Typs in eine Klasse

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Konvertieren eines anonymen Typs in eine Klasse

**Hintergrund:** Sie verfügen über einen anonymen Typ, den Sie in einer Klasse weiterentwickeln möchten.

**Vorteile**: Anonyme Typen sind nützlich, wenn Sie sie nur lokal verwenden. Sobald Ihr Code komplexer wird, ist es von Vorteil, Typen einfach zu Klassen heraufzustufen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einem anonymen Typ.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Konvertieren eines anonymen Typs in eine Klasse](media/convert-anon-to-class.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

   ![Die Konvertierung eines anonymen Typs in eine Klasse wurde akzeptiert](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
