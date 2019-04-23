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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053396"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Der zu codierende URI enthält ein ungültiges Zeichen.
Sie haben versucht, eine Zeichenfolge als URI (Uniform Resource Identifier) zu codieren, aber es ungültige Zeichen enthalten. Obwohl die meisten Zeichen innerhalb von Zeichenfolgen in URIs konvertiert werden ungültig sind, sind einige Unicode-Zeichenfolgen nicht zulässig.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass nur gültige Unicode-Zeichenfolgen enthält, die zu codierende Zeichenfolge. Ein vollständigen URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die Namen in spitzen Klammern stehen für Komponenten, und die ":", "/", ";" und "?" sind reservierte Zeichen als Trennzeichen verwendet. Das allgemeine Format lautet:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [EncodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)