---
title: Boolescher Wert erwartet. | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82123fe2a38b3de1d6e6c015f47bc5f7edd02791
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840517"
---
# <a name="boolean-expected"></a>Boolescher Wert erwartet
Sie haben versucht, rufen Sie die **Boolean.prototype.toString** oder **Boolean.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `Boolean`. Das Objekt dieser Art von Aufruf muss vom Typ `Boolean`. Zum Beispiel:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Rufen Sie nur die **Boolean.prototype.toString** oder **Boolean.prototype.valueOf** Methoden für Objekte vom Typ **Boolean.**

## <a name="see-also"></a>Siehe auch

- [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)
- [Datentypen](../../javascript/data-types-javascript.md)
- [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)
- [Kopieren, Übergeben und Vergleichen von Daten](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)