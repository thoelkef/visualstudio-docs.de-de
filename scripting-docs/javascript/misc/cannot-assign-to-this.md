---
title: Nicht zugewiesen &#39;dies&#39; | Microsoft-Dokumentation
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
ms.openlocfilehash: 47e55d39e85675b37d2ac9741d1207a9e81d369e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856647"
---
# <a name="cannot-assign-to-39this39"></a>Nicht zugewiesen &#39;dies&#39;
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