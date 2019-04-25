---
title: Umkehren von if-Anweisungen
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5a809eee1eb5460e245f64156385f759870adbd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970257"
---
# <a name="invert-if-statement"></a>Umkehren von if-Anweisungen

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht Ihnen das Umkehren einer `if`- oder `if else`-Anweisung, ohne die Bedeutung des Codes zu ändern.

**Hintergrund:** Wenn Sie über eine `if`- oder `if else`-Anweisung verfügen, die verständlicher wäre, wenn sie umgekehrt wäre.

**Vorteile**: Das manuelle Umkehren einer `if`- oder `if else`-Anweisung kann sehr viel länger dauernd und Fehler verursachen. Dieser Codefix unterstützt Sie dabei, dieses Refactoring automatisch durchzuführen.

## <a name="invert-if-statement-refactoring"></a>Refactoring: Invertieren von if-Anweisungen

1. Platzieren Sie den Cursor in einer `if`- oder `if else`-Anweisung.

    ![if else-Anweisung umkehren](media/invert-if.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Codefix zum Umkehren einer if else-Anweisung](media/invert-if-codefix.png)

3. Wählen Sie **if umkehren** aus.

    ![Ergebnis des Umkehrens einer if else-Anweisung](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)
