---
title: Hochstufen von Membern in der Hierarchie
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969167"
---
# <a name="pull-members-up"></a>Hochstufen von Membern in der Hierarchie

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Member sollen in den Basistyp hochgestuft werden.

**Hintergrund:** Sie haben eine Schnittstelle implementiert und möchten einen Member in den Basistyp verschieben.

**Vorteile**: Wenn Sie Member in der Hierarchie hochstufen, können andere Implementierungen Ihrer Schnittstelle diese Member ebenfalls erben.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf einem beliebigen Member einer implementierten Schnittstelle.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Hochstufen von Membern in der Hierarchie](media/pull-members-up.png)

2. Klicken Sie auf **Pull Members up to base type** (Member in den Basistyp hochstufen).

3. Wählen Sie im Dialogfeld aus, welche Member der ausgewählten Schnittstelle hinzugefügt werden sollen.

   ![Hochstufen eines Members in der Hierarchie](media/pull-members-up-dialog.png)

4. Klicken Sie auf **OK**. Die ausgewählten Member werden auf die Schnittstelle hochgestuft.

   ![Vollständiges Hochstufen von Membern in der Hierarchie](media/pull-members-up-completed.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
