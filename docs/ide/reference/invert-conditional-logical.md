---
title: Invertieren von bedingten Ausdrücken und logischen Operationen
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
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157359"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertieren von bedingten Ausdrücken und bedingten UND/ODER-Operatoren

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht das Invertieren von bedingten Ausdrücken oder bedingten UND/ODER-Operatoren.

**Hintergrund:** Sie haben einen bedingten Ausdruck oder einen bedingten UND/ODER-Operator, der in invertierter Form besser verstanden würde.

**Vorteile**: Einen Ausdruck oder einen bedingten UND/ODER-Operator manuell zu invertieren ist zeitaufwändiger. Außerdem könnten dabei Fehler eingeführt werden. Dieser Codefix unterstützt Sie dabei, dieses Refactoring automatisch durchzuführen.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Umkehren von bedingten Ausdrücken und Refactoring von bedingten UND/ODER-Operatoren

1. Platzieren Sie Ihren Cursor in einen bedingten Ausdruck oder einen bedingten UND/ODER-Operator.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Invert conditional** (Bedingung invertieren) aus oder **ersetzen Sie '&&' mit '||'**.

    ![Umkehren einer Bedingung](media/invert-conditional.png)

    ![Umkehren einer Bedingung](media/invert-logical-operator.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)
