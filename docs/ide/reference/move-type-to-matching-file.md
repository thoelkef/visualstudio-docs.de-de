---
title: Verschieben eines Typs in ein entsprechendes Dateirefactoring in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 62187c88fa2d2cf7ecf1b358fa0c03416be449a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Verschieben eines Typs in ein entsprechendes Dateirefactoring

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie den ausgewählten Typ in eine separate Datei mit demselben Namen verschieben.

**Hintergrund**: Es sind mehrere Klassen, Strukturen, Schnittstellen usw. in der gleichen Datei vorhanden, die Sie trennen möchten.

**Vorteile**: Das Platzieren mehrerer Typen in die gleiche Datei kann die Suche nach diesen Typen erschweren. Durch das Verschieben von Typen in Dateien mit demselben Namen wird der Code besser lesbar und ist einfacher zu navigieren.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen des zu verschiebenden Typs, oder platzieren Sie den Textcursor in den Namen:

   - C#:

    ![Hervorgehobener Code – C#](media/movetype-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code – Visual Basic](media/movetype-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Typ in *TypeName*.cs verschieben** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
   - **Maus**
     - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Typ in *TypeName*.cs verschieben** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.

   Der Typ wird als Bestandteil Ihrer Projektmappe in eine neue Datei mit diesem Namen verschoben.

   - C#:

    ![Ergebnis des Inlinevorgangs in C#](media/movetype-result-cs.png)

   - Visual Basic:

    ![Ergebnis des Inlinevorgangs in Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)