---
title: Umschließen und Ausrichten von Aufrufketten
description: Erfahren Sie, wie Sie Ketten von Methodenaufrufen umschließen und ausrichten.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620012"
---
# <a name="wrap-and-align-call-chains"></a>Umschließen und Ausrichten von Aufrufketten

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Ermöglicht das Umschließen und Ausrichten von Ketten von Methodenaufrufen.

**Hintergrund:** Sie verwenden eine lange Kette, die aus mehreren Methodenaufrufen in einer Anweisung besteht.

**Vorteile**: Eine lange Liste ist einfacher zu lesen, wenn sie den Benutzereinstellungen entsprechend umschlossen oder eingezogen ist.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einer beliebigen Aufrufkette.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Aufrufkette umbrechen** oder **Aufrufkette umbrechen und ausrichten** aus, um das Refactoring zu akzeptieren.

   ![Umschließen und Ausrichten von Aufrufketten](media/wrap-call-chain.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
