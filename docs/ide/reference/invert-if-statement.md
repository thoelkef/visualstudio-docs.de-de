---
title: Umkehren von if-Anweisungen
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6dd0a3ebdb41243734850cea4f4b43604ebb94b
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324665"
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
