---
title: Der URI, der decodiert werden soll, ist keine gültige Codierung. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98d2ee08a52e86c435c58502da1ab4f68b594905
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816162"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Der zu decodierende URI weist keine gültige Codierung auf.
Sie haben versucht, einen nicht ordnungsgemäß formatierten URI (Uniform Resource Identifier) zu decodieren. URIs haben eine spezielle Syntax. die meisten nicht-alphanumerischen Zeichen müssen codiert werden, bevor Sie in einem URI verwendet werden können. Sie können die `encodeURI` -Methode und die- `encodeURIComponent` Methode verwenden, um einen URI aus einer normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolge zu erstellen.  
  
 Ein kompletter URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die allgemeine Form ist:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Die Namen in spitzen Klammern stellen Komponenten dar, und ":", "/", ";" und "?" sind reservierte Zeichen, die als Trennzeichen verwendet werden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass Sie nur gültige URIs decodieren. Normale Zeichen folgen können nicht decodiert [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] werden, da Sie möglicherweise ungültige Zeichen enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [decodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)