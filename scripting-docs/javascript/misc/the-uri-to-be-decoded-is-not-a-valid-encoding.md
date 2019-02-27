---
title: Die zu decodierende URI ist keine gültige Codierung | Microsoft-Dokumentation
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
ms.openlocfilehash: 792403a9a53f11431e87115d7a95345e316dc2ac
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844294"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Der zu decodierende URI weist keine gültige Codierung auf.
Sie haben versucht, einen nicht ordnungsgemäß formatierten URI (Uniform Resource Identifier) zu decodieren. URIs haben eine spezielle Syntax; Die meisten nicht-alphanumerischen Zeichen müssen codiert werden, bevor sie in einem URI verwendet werden können. Sie können die `encodeURI` und `encodeURIComponent` Methoden zum Erstellen eines URI einer normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolge.  
  
 Ein vollständigen URI besteht aus einer Sequenz von Komponenten und Trennzeichen. Das allgemeine Format lautet:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Die Namen in spitzen Klammern stehen für Komponenten, und die ":", "/", ";" und "?" sind reservierte Zeichen als Trennzeichen verwendet.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass Sie nur gültige URIs decodieren möchten. Sie konnte nicht decodiert normalen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Zeichenfolgen, da sie ungültige Zeichen enthalten können.  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)