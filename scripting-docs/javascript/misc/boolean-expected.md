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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862661"
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

- [Boolean-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Datentypen](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Steuern des Programmablaufs](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Kopieren, Übergeben und Vergleichen von Daten](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)