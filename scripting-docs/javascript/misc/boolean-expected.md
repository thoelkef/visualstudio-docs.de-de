---
title: Boolescher Wert erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576056"
---
# <a name="boolean-expected"></a>Boolescher Wert erwartet
Sie haben versucht, die Methode " **Boolean. Prototype. ToString** " oder " **Boolean. Prototype. valueOf** " für ein Objekt eines anderen Typs als "`Boolean`" aufzurufen. Das Objekt dieses Aufruf Typs muss vom Typ "`Boolean`" sein. Beispiel:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Rufen Sie nur die Methoden " **Boolean. Prototype. ToString** " oder " **Boolean. Prototype. valueOf** " für Objekte vom Typ " **Boolean** " auf.

## <a name="see-also"></a>Siehe auch

- [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)
- [Datentypen](../../javascript/data-types-javascript.md)
- [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)
- [Kopieren, Übergeben und Vergleichen von Daten](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)