---
title: Hinzufügen einer expliziten Umwandlung
ms.date: 03/26/2020
ms.topic: reference
author: y87feng
ms.author: t-yufen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a61a8ed782df935a146b111bbc4107fa7c6d82
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2020
ms.locfileid: "80416843"
---
# <a name="add-explicit-cast"></a>Hinzufügen einer expliziten Umwandlung

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Mit diesem Feature können Sie eine explizite Umwandlung basierend auf der Nutzung automatisch zu einem Ausdruck hinzufügen.

**Hintergrund:** Sie können dieses Feature verwenden, wenn Sie eine explizite Umwandlung zu einem Ausdruck hinzufügen müssen und diese automatisch zuweisen möchten.

**Vorteile**: Sie könnten eine explizite Umwandlung auch manuell zu einem Ausdruck hinzufügen, jedoch fügt dieses Feature sie basierend auf den Codekontext automatisch hinzu.

## <a name="how-to-use-it"></a>Verwendungsweise

1. Platzieren Sie das Caretzeichen im Fehler.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Klicken Sie auf **Add explicit cast** (Explizite Umwandlung hinzufügen).

   ![Schnellaktion zum Hinzufügen einer expliziten Umwandlung in Visual Studio](media/add-explicit-cast.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Refactoring](../refactoring-in-visual-studio.md)
