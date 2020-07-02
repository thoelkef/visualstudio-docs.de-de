---
title: Der zu codierende URI enthält ein ungültiges Zeichen | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816071"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Der zu codierende URI enthält ein ungültiges Zeichen.
Sie haben versucht, eine Zeichenfolge als URI (Uniform Resource Identifier) zu codieren, enthielt jedoch ungültige Zeichen. Obwohl die meisten Zeichen in Zeichen folgen gültig sind, die in URIs konvertiert werden, sind einige Unicode-Zeichen folgen unzulässig.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die zu codierende Zeichenfolge nur gültige Unicode-Sequenzen enthält. Ein kompletter URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die Namen in spitzen Klammern stellen Komponenten dar, und ":", "/", ";" und "?" sind reservierte Zeichen, die als Trennzeichen verwendet werden. Die allgemeine Form ist:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Encode URI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)