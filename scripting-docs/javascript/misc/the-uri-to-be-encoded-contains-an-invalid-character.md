---
title: Die zu codierende URI enthält ein ungültiges Zeichen | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832173"
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