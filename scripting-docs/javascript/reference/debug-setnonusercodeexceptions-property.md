---
title: Debug.setNonUserCodeExceptions-Eigenschaft | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636160"
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions-Eigenschaft
Bestimmt, ob alle Try / Catch-Blocks in diesem Bereich werden vom Debugger als vom Benutzercode unbehandelt behandelt werden soll. Ausnahmen können eingeteilt, vom Benutzercode unbehandelt ausgelöst oder nicht behandelt werden.  
  
 Wenn diese Eigenschaft, um festgelegt wird `true` in einem bestimmten Bereich der Debugger kann dann bestimmen, einige Maßnahmen (z. B. unterbrechen) auf Ausnahmen innerhalb dieses Bereichs ausgelöst wird, wenn der Entwickler möchte auf Ausnahmen vom Benutzercode unbehandelt unterbrechen. Wenn diese Eigenschaft, um festgelegt wird `false` identisch ist, als ob die Eigenschaft nicht festgelegt wurde.  
  
 Weitere Informationen zum Debuggen finden Sie unter [Active Script-Übersicht zum Debuggen](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie diese Eigenschaft festgelegt wird.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]