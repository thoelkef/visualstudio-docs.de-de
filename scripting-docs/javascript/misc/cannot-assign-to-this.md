---
title: Zuweisen zu "This" nicht möglich | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
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
ms.openlocfilehash: 73baa77cc63e3a43ac30e70f66081bbc7ade3020
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572350"
---
# <a name="cannot-assign-to-this"></a>Zuweisen zu „this“ nicht möglich
Sie haben versucht, **dieser**einen Wert zuzuweisen. **Dies** ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Schlüsselwort, das auf Folgendes verweist:

- das Objekt, das derzeit eine Methode ausführt.

- das globale Objekt, wenn keine aktuelle Methode vorhanden ist (oder die Methode keinem anderen Objekt angehört).

Eine Methode ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Funktion, die durch ein-Objekt aufgerufen wird. Innerhalb einer Methode ist das **this** -Schlüsselwort ein Verweis auf das Objekt, über das die Methode aufgerufen wurde (Dies ist das Objekt, das durch Aufrufen des-Klassenkonstruktors mit dem **New** -Operator erstellt wurde).

In einer Methode können Sie **diese** verwenden, um auf das aktuelle-Objekt zu verweisen, Sie können **diesem**jedoch keinen neuen Wert zuweisen.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Versuchen Sie nicht, **diesen**zuzuweisen. Wenn Sie auf eine Eigenschaft oder Methode eines instanziierten Objekts zugreifen möchten, verwenden Sie den Punkt Operator (z. b. **Circle. Radius**).

  > [!NOTE]
  > Sie können eine vom Benutzer **erstellte Variable nicht**benennen. Es handelt sich um ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] reserviertes Wort.

## <a name="see-also"></a>Siehe auch

- [this-Anweisung](../../javascript/reference/this-statement-javascript.md)
- [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)