---
title: Zuweisen zu "This" nicht möglich | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 8985c7201a8e315353dd89ab5e1f5a3ad3b403ea
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862768"
---
# <a name="cannot-assign-to-this"></a>Zuweisen zu „this“ nicht möglich
Sie haben versucht, **dieser**einen Wert zuzuweisen. **Dies** ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Schlüsselwort, das auf eine der folgenden Optionen verweist:

- das Objekt, das derzeit eine Methode ausführt.

- das globale Objekt, wenn keine aktuelle Methode vorhanden ist (oder die Methode keinem anderen Objekt angehört).

Eine Methode ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Funktion, die durch ein-Objekt aufgerufen wird. Innerhalb einer Methode ist das **this** -Schlüsselwort ein Verweis auf das Objekt, über das die Methode aufgerufen wurde (Dies ist das Objekt, das durch Aufrufen des-Klassenkonstruktors mit dem **New** -Operator erstellt wurde).

In einer Methode können Sie **diese** verwenden, um auf das aktuelle-Objekt zu verweisen, Sie können **diesem**jedoch keinen neuen Wert zuweisen.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Versuchen Sie nicht, **diesen**zuzuweisen. Wenn Sie auf eine Eigenschaft oder Methode eines instanziierten Objekts zugreifen möchten, verwenden Sie den Punkt Operator (z. b. **Circle. Radius**).

  > [!NOTE]
  > Sie können eine vom Benutzer **erstellte Variable nicht**benennen. Es ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] reserviertes Wort.

## <a name="see-also"></a>Weitere Informationen

- [Diese Anweisung](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/this)
- [Problembehandlung bei Skripts](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)