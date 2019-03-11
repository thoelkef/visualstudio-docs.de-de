---
title: Nicht verwendete Werte und Parameter
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ea80887fff6dcb1afba80feb782b23d1e790579
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325025"
---
# <a name="unused-expression-values-and-parameters"></a>Nicht verwendete Ausdruckswerte und Parameter

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Nicht verwendete Parameter werden ausgeblendet, und eine Warnung für nicht verwendete Ausdruckswerte generiert.

**Hintergrund:** Sie haben Parameter oder Ausdruckswerte, die nicht verwendet werden.

**Vorteile**: Manchmal ist es gar nicht so einfach, zu bestimmen, ob ein Wert oder Parameter noch verwendet wird. Indem diese Werte ausgeblendet werden, oder ein Warnhinweis gegeben wird, erhalten Sie einen sichtbaren Hinweis darauf, welchen Code Sie löschen können.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnose nicht verwendeter Ausdruckswerte und Parameter

1. Gibt es Ausdruckswerte oder Parameter, die nicht verwendet werden?
2. Die nicht verwendeten Parameter werden ausgeblendet. Für die nicht verwendeten Ausdruckswert wird eine Warnung ausgegeben.

  ![Nicht verwendeter Parameter](media/unused-parameter.png)
  ![Nicht verwendeter Wert](media/unused-value.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)
