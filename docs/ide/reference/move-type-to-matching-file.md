---
title: Verschieben eines Typs in ein entsprechendes Dateirefactoring
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1cdb84af563afaf5b51d3c378d7a9e06d67a9e76
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039084"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Verschieben eines Typs in ein entsprechendes Dateirefactoring

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie den ausgewählten Typ in eine separate Datei mit demselben Namen verschieben.

**Hintergrund:** Es sind mehrere Klassen, Strukturen, Schnittstellen usw. in der gleichen Datei vorhanden, die Sie trennen möchten.

**Vorteile**: Das Platzieren mehrerer Typen in die gleiche Datei kann die Suche nach diesen Typen erschweren. Durch das Verschieben von Typen in Dateien mit demselben Namen wird der Code besser lesbar und ist einfacher zu navigieren.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb des Namens des Typs, wo dieser definiert wird. Beispiel:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Führen Sie dann eine der folgenden Aktionen aus:

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**,
   - Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Schnellaktionen und Refactorings** aus.

1. Wählen Sie **Typ verschieben in *TypeName*cs** aus dem Menü aus. Dabei ist *TypeName* der Name des Typs, den Sie ausgewählt haben.

   Der Typ wird in eine neue Datei im Projekt verschoben, die den gleichen Namen wie der Typ aufweist.

   - C#:

      ![Ergebnis des Inlinevorgangs in C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Ergebnis des Inlinevorgangs in Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
