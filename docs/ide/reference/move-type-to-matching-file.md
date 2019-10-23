---
title: Verschieben eines Typs in ein entsprechendes Dateirefactoring
description: Verschieben Sie einen Typ in eine separate Datei mit demselben Namen. Klicken Sie mit der rechten Maustaste auf den Typ, wählen Sie Schnellaktionen und Refactorings aus, und klicken Sie auf „Typ in <TypeName>.cs verschieben“.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba822981ade5ebdc191732e0a32b02a9a4005fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666485"
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

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** ,
   - Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Schnellaktionen und Refactorings** aus.

1. Wählen Sie **Typ verschieben in *TypeName*cs** aus dem Menü aus. Dabei ist *TypeName* der Name des Typs, den Sie ausgewählt haben.

   Der Typ wird in eine neue Datei im Projekt verschoben, die den gleichen Namen wie der Typ aufweist.

   - C#:

      ![Ergebnis des Inlinevorgangs in C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Ergebnis des Inlinevorgangs in Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
