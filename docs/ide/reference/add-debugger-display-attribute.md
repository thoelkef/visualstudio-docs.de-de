---
title: Hinzufügen des Attributs DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290847"
---
# <a name="add-debuggerdisplay-attribute"></a>Hinzufügen des Attributs DebuggerDisplay

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Das [Attribut DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) steuert die Anzeige von Objekten, Eigenschaften oder Feldern in den Variablenfenstern des Debuggers.

**Hintergrund:** Sie möchten im Debugger [Eigenschaften programmgesteuert in Ihrem Code anheften](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips).

**Vorteile**: Das Anheften von Eigenschaften ermöglicht Ihnen, Objekte schnell anhand ihrer Eigenschaften zu untersuchen, indem Sie diese Eigenschaft im Debugger an den Anfang der Eigenschaftsliste des Objekts setzen. 

## <a name="how-to"></a>Vorgehensweise

1. Positionieren Sie den Cursor entweder auf einem Typ, Delegaten, einer Eigenschaft oder einem Feld. 

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie **Attribut DebuggerDisplay hinzufügen** aus.

    ![Vergleichsoperatoren generieren](media/add-debugger-display-attribute.png)

3. Das Attribut DebuggerDisplay wird zusammen mit einer Auto-Methode hinzugefügt, die standardmäßig ToString() zurückgibt. 

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
