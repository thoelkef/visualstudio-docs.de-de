---
title: Nicht zugewiesen "this" | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f147e591969f803533bb23ff16d73ee9af2c3d27
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839788"
---
# <a name="cannot-assign-to-this"></a>Zuweisen zu „this“ nicht möglich
Sie haben versucht, einen Wert zuzuweisen **dies**. **Dies** ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Schlüsselwort, das entweder verweist:

- das Objekt derzeit Ausführen einer Methode

- das globale Objekt, wenn keine aktuelle Methode vorhanden ist (oder die Methode nicht mit jedem anderen Objekt gehört).

Eine Methode ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Funktion, die durch ein Objekt aufgerufen wird. Innerhalb einer Methode die **dies** Schlüsselwort ist ein Verweis auf das Objekt über die Methode aufgerufen wurde (dies der Fall. um das Objekt erstellt, durch den Aufruf des Klassenkonstruktors mit der **neue** Operator).

Innerhalb einer Methode, können Sie **dies** zum Verweisen auf das aktuelle Objekt, aber Sie können keinen neuen Wert zuweisen **dies**.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Versuchen Sie nicht zuweisen **dies**. Zugriff auf eine Eigenschaft oder Methode eines instanziierten Objekts verwenden Sie den Punktoperator (z. B. **circle.radius**).

  > [!NOTE]
  > Sie können nicht den Namen einer Variablen benutzererstellte **dies**; es ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] reserviertes Wort.

## <a name="see-also"></a>Siehe auch

- [this-Anweisung](../../javascript/reference/this-statement-javascript.md)
- [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)