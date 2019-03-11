---
title: Verwenden von Lambdaausdrücken oder Blocktext
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 01ea32ffe978d7b1544597857187f00bec9c3467
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324765"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Verwenden von Ausdruckskörpern oder Blocktext für Lambdaausdrücke

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Lambdaausdrücke können umgestaltet werden, sodass ein Ausdruckskörper oder Blocktext verwendet werden.

**Hintergrund:** Wenn Sie es bevorzugen, dass Lambdaausdrücke entweder ein Ausdruckskörper oder Blocktext verwenden. 

**Vorteile**: Lambdaausdrücke können umgestaltet werden, um die Lesbarkeit gemäß der Wünsche Ihrer Benutzer zu verbessern.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactoring von Lambdaausdruckskörpern oder Ausdruckskörpern

1. Platzieren Sie Ihren Cursor rechts auf einem Lambdaoperator.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

  ![Verwenden von Lambdaausdrücken/Blocktext](media/block-body-lambda.png)

3. Wählen Sie **Use block for lambda expressions** (Block für Lambdaausdrücke verwenden) oder **Use expression body for lambda expressions** (Ausdruckskörper für Lambdaausdrücke verwenden) aus.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)