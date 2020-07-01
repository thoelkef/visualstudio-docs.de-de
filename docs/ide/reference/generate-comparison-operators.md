---
title: Generieren von Vergleichsoperatoren für Typen, die IComparable implementieren
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290835"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Generieren von Vergleichsoperatoren für Typen, die IComparable implementieren

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Sie können jetzt **Vergleichsoperatoren** für Typen generieren, die IComparable implementieren.

**Hintergrund:** Sie verfügen über einen Typ, der IComparable implementiert. Wir fügen die Vergleichsoperatoren automatisch hinzu.

**Vorteile**: Wenn Sie einen Werttyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, um eine bessere Leistung als mit der Standardimplementierung der Equals-Methode in ValueType zu erzielen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor entweder innerhalb der Klasse oder auf dem Schlüsselwort IComparable.

2. Führen Sie dann eine der folgenden Aktionen aus:

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.

   - Klicken Sie auf die Schaltfläche ![Schraubendrehersymbol](../media/screwdriver-icon.png) am linken Rand

   ![Generieren von Vergleichsoperatoren](media/generate-comparison-operators.png)

3. Wählen Sie im Dropdownmenü **Equals(object) generieren** aus.

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
