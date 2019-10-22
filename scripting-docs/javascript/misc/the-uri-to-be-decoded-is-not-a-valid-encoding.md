---
title: Der URI, der decodiert werden soll, ist keine gültige Codierung. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572263"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Der zu decodierende URI weist keine gültige Codierung auf.
Sie haben versucht, einen nicht ordnungsgemäß formatierten URI (Uniform Resource Identifier) zu decodieren. URIs haben eine spezielle Syntax. die meisten nicht-alphanumerischen Zeichen müssen codiert werden, bevor Sie in einem URI verwendet werden können. Sie können die Methoden `encodeURI` und `encodeURIComponent` verwenden, um einen URI aus einer normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolge zu erstellen.  
  
 Ein kompletter URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Die allgemeine Form ist:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Die Namen in spitzen Klammern stellen Komponenten dar, und ":", "/", ";" und "?" sind reservierte Zeichen, die als Trennzeichen verwendet werden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass Sie nur gültige URIs decodieren. Sie können keine normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolgen decodieren, da Sie möglicherweise ungültige Zeichen enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [decodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)    
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)