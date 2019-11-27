---
title: "\"@\" Erwartet | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576515"
---
# <a name="expected-"></a>Es wurde "\@" erwartet.
Sie haben versucht, eine Variable zu erstellen, die mit Anweisungen für die bedingte Kompilierung verwendet wird, indem Sie die `@set`-Anweisung verwenden, aber vor dem Variablennamen keinen mit dem Vorzeichen " **@** " platziert haben.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie ein am Zeichen " **@** " direkt vor dem Variablennamen ein. Beispiel:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)   
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)
