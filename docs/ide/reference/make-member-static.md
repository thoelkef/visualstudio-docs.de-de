---
title: Festlegen eines Members als statisch
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77519302"
---
# <a name="make-member-static"></a>Festlegen eines Members als statisch

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Festlegen eines Members als statisch

**Hintergrund:** Wenn Sie einen nicht statischen Member als statisch festlegen möchten

**Vorteile**: Statische Member verbessern die Lesbarkeit: Wenn bekannt ist, dass spezifischer Code isoliert ist, ist dieser einfacher zu verstehen, wieder zu lesen und wiederzuverwenden. 

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie das Caretzeichen im Membernamen.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Festlegen eines Members als statisch](media/make-member-static.png)

3. Klicken Sie auf **Als statisch festlegen**.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
