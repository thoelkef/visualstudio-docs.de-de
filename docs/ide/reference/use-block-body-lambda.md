---
title: Verwenden von Lambdaausdrücken oder Blocktext
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1f055925a4da916bf88da802e7a4991b0362b057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789428"
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