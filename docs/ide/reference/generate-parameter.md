---
title: Refactoring der Parametergenerierung
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329060"
---
# <a name="generate-parameter"></a>Parameter generieren

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit wird automatisch ein Methodenparameter generiert.

**Hintergrund:** Sie verweisen auf eine Variable in einer Methode, die im aktuellen Kontext nicht vorhanden ist, und erhalten eine Fehlermeldung. Zur Codefehlerbehebung können Sie einen Parameter generieren. 

**Vorteile**: Sie können eine Methodensignatur schnell und ohne Verlust von Kontext ändern.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in den Variablennamen, und drücken Sie **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
1. Wählen Sie **Parameter generieren** aus.

   ![Parameter generieren](media/generate-parameter.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
