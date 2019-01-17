---
title: Boolescher Wert erwartet. | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347930"
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