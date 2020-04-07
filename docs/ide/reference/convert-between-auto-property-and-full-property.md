---
title: Konvertieren zwischen automatischen und vollständigen Eigenschaften
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395736"
---
# <a name="convert-between-auto-property-and-full-property"></a>Konvertieren zwischen automatischen und vollständigen Eigenschaften

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Dieses Feature dient zum Konvertieren von automatisch implementierten Eigenschaften in vollständige Eigenschaften.

**Hintergrund:** Die Logik der Eigenschaft wurde geändert.

**Vorteile**: Sie können eine automatisch implementierte Eigenschaft auch manuell in eine vollständige Eigenschaft konvertieren, jedoch führt dieses Feature diesen Vorgang automatisch für Sie durch. 

## <a name="how-to"></a>Vorgehensweise

1. Zeigen Sie mit dem Cursor auf den Namen der Eigenschaft.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie eine der folgenden beiden Optionen aus: 

    Wählen Sie die Option **In vollständige Eigenschaft konvertieren** aus.

   ![Konvertieren der Auto-Eigenschaft in eine vollständige Eigenschaft](media/convert-auto-property-to-full-property.png) 

    Wählen Sie die Option **Automatisch generierte Eigenschaft verwenden** aus. 

    ![Konvertieren der vollständigen Eigenschaft in eine automatische Eigenschaft](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
