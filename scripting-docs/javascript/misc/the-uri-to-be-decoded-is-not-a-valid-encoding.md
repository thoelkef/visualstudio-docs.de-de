---
title: Die zu decodierende URI weist keine gültige Codierung | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633330"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Der zu decodierende URI weist keine gültige Codierung auf.
Sie haben versucht, einen nicht ordnungsgemäß formatierter URI (Uniform Resource Identifier) zu decodieren. URIs haben eine spezielle Syntax; Die meisten nicht-alphanumerische Zeichen müssen codiert werden, bevor sie in einem URI verwendet werden können. Sie können die `encodeURI` und `encodeURIComponent` Methoden So erstellen Sie einen URI aus einer normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolge.  
  
 Ein vollständiger URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Das allgemeine Format ist:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Die Namen in spitzen Klammern stellen Komponenten dar, und die ":", "/", ";" und "?" sind reservierte Zeichen als Trennzeichen verwendet.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass nur gültige URIs codiert werden soll. Sie können nicht decodiert werden normale [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolgen, da sie möglicherweise ein ungültige Zeichen enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)