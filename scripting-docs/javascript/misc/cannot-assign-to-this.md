---
title: Nicht zugewiesen "this" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f47778075b0395e4f0791d8f485188d40fab87a4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344173"
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