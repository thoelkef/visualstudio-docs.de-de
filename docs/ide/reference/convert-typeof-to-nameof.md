---
title: Konvertieren von typeof in nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 233393114883c2a9833aa7ec82f0d78f0ef33bae
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251329"
---
# <a name="convert-typeof-to-nameof"></a>Konvertieren von `typeof` in `nameof`

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht das Konvertieren einer Instanz von `typeof(<QualifiedType>).Name` in `nameof(<QualifiedType>)` in C# und einer Instanz von `GetType(<QualifiedType>).Name` in `NameOf(<QualifiedType>)` in Visual Basic.

**Hintergrund:**  Alle Instanzen von `typeof(<QualifiedType>).Name`, bei denen `someType` kein generischer Typ ist. Dieser Ausschluss ist erforderlich, da in diesem Fall nicht der gleiche Zeichenfolgenwert als `nameof(<QualifiedType>)`zurückgegeben wird. Gleiches gilt für die Visual Basic-Instanz.

**Vorteile**: Die Verwendung von `nameof` anstelle des Namens des `type` vermeidet die Reflexion, die mit dem Abrufen eines `type`-Objekts verbunden ist, und es ist eine pragmatischere Methode der Programmierung.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb der `typeof(<QualifiedType>).Name`-Instanz für C# oder in `GetType(<QualifiedType>).Name` in Visual Basic.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie eine der folgenden Optionen aus:

- C#
  <br>Wählen Sie **„typeof“ in „nameof“ konvertieren**aus.
  ![„typeof“ in „nameof“ konvertieren](media/convert-type-of.PNG)

- Visual Basic
  <br>Wählen Sie **„GetType“ in „NameOf“ konvertieren** aus.![“typeof“ in „nameof“ konvertieren](media/convert-get-type.PNG)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
