---
title: "Der zu codierende URI enthält ein ungültiges Zeichen | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Der zu codierende URI enthält ein ungültiges Zeichen.
Sie haben versucht, eine Zeichenfolge zu codieren, als URI (Uniform Resource Identifier), aber es ungültige Zeichen enthalten. Obwohl die meisten Zeichen in Zeichenfolgen zu konvertierenden URIs gültig sind, sind einige Unicode-Zeichenfolgen nicht zulässig.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die zu codierende Zeichenfolge nur gültige Unicode-Zeichenfolgen enthält. Ein vollständiger URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die Namen in spitzen Klammern stellen Komponenten dar, und die ":", "/", ";" und "?" sind reservierte Zeichen als Trennzeichen verwendet. Das allgemeine Format ist:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [EncodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)