---
title: Boolescher Wert erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817670"
---
# <a name="boolean-expected"></a>Boolescher Wert erwartet
Sie haben versucht, die **Boolean. Prototype. ToString** -Methode oder die **Boolean. Prototype. valueOf** -Methode für ein Objekt eines anderen Typs als aufzurufen `Boolean` . Das Objekt dieses Aufruf Typs muss vom Typ sein `Boolean` . Beispiel:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Rufen Sie nur die Methoden " **Boolean. Prototype. ToString** " oder " **Boolean. Prototype. valueOf** " für Objekte vom Typ " **Boolean** " auf.

## <a name="see-also"></a>Weitere Informationen

- [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)
- [Datentypen](../../javascript/data-types-javascript.md)
- [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)
- [Kopieren, Übergeben und Vergleichen von Daten](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)