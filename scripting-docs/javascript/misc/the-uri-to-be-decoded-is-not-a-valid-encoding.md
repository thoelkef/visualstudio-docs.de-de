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
ms.openlocfilehash: 38ea642cece501804b6ee2efaac778c3b8d520fc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861869"
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
 [decodeURI-Funktion](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent-Funktion](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)