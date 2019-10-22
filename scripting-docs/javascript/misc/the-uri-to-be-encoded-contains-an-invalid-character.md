---
title: Der zu codierende URI enthält ein ungültiges Zeichen | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 72fd550e27e64754fe8c4857e9aa4d25ae5711a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572250"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Der zu codierende URI enthält ein ungültiges Zeichen.
Sie haben versucht, eine Zeichenfolge als URI (Uniform Resource Identifier) zu codieren, enthielt jedoch ungültige Zeichen. Obwohl die meisten Zeichen in Zeichen folgen gültig sind, die in URIs konvertiert werden, sind einige Unicode-Zeichen folgen unzulässig.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die zu codierende Zeichenfolge nur gültige Unicode-Sequenzen enthält. Ein kompletter URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die Namen in spitzen Klammern stellen Komponenten dar, und ":", "/", ";" und "?" sind reservierte Zeichen, die als Trennzeichen verwendet werden. Die allgemeine Form ist:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
   der [encode URI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)  
 [encodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)