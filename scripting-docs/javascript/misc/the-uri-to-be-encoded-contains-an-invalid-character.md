---
title: Die zu codierende URI enthält ein ungültiges Zeichen | Microsoft-Dokumentation
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
ms.openlocfilehash: a3c71b90d0711bf317d0ed72d51c0d5d45297c80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841869"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Der zu codierende URI enthält ein ungültiges Zeichen.
Sie haben versucht, eine Zeichenfolge als URI (Uniform Resource Identifier) zu codieren, aber es ungültige Zeichen enthalten. Obwohl die meisten Zeichen innerhalb von Zeichenfolgen in URIs konvertiert werden ungültig sind, sind einige Unicode-Zeichenfolgen nicht zulässig.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass nur gültige Unicode-Zeichenfolgen enthält, die zu codierende Zeichenfolge. Ein vollständigen URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die Namen in spitzen Klammern stehen für Komponenten, und die ":", "/", ";" und "?" sind reservierte Zeichen als Trennzeichen verwendet. Das allgemeine Format lautet:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [EncodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)