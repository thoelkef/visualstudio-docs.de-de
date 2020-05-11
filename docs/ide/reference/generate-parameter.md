---
title: Refactoring der Parametergenerierung
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094359"
---
# <a name="generate-parameter"></a>Parameter generieren

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit wird automatisch ein Methodenparameter generiert.

**Hintergrund:** Sie verweisen auf eine Variable in einer Methode, die im aktuellen Kontext nicht vorhanden ist, und erhalten eine Fehlermeldung. Zur Codefehlerbehebung können Sie einen Parameter generieren. 

**Vorteile**: Sie können eine Methodensignatur schnell und ohne Verlust von Kontext ändern.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in den Variablennamen, und drücken Sie **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
1. Wählen Sie **Parameter generieren** aus.

   ![Parameter generieren](media/generate-parameter.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
