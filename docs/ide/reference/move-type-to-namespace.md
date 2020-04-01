---
title: Verschieben eines Typs in den Namespace
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
monikerRange: vs-2019
ms.openlocfilehash: 58d2757fa8798b67c8e597f5f82bc65a279f4a90
ms.sourcegitcommit: 8ff6c6975148ce43bdac21c8995fbab910c312fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375566"
---
# <a name="move-type-to-namespace"></a>Verschieben eines Typs in den Namespace

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Verschieben eines Typs in den Namespace.

**Hintergrund:** Sie möchten einen Typ in einen anderen Namespace oder Ordner verschieben. 

**Vorteile**: Sie möchten Teile Ihrer Projektmappe umgestalten und eine schnelle Möglichkeit finden, einen Typ in einen anderen Namespace oder Ordner zu verschieben. 

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf dem Klassenname.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **In Namespace verschieben** aus.

   ![Umgestalten: In Namespace verschieben](media/move-to-namespace.png)

4. Wählen Sie im geöffneten Dialogfeld den Zielnamespace aus, in den Sie den Typ verschieben möchten. 

   ![Dialogfeld „Namespace auswählen“](media/select-target-namespace.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
