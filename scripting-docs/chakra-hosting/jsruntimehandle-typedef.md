---
title: JsRuntimeHandle-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568710"
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle-TypeDef
Ein Handle für eine Chakra-Laufzeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Hinweise  
 Jede Chakra-Laufzeit hat ihre eigene unabhängige Ausführungsengine, ihren eigenen JIT-Compiler und ihren eigenen Heap mit Garbage Collection. Daher ist jede Laufzeit vollständig von anderen Laufzeiten isoliert.  
  
 Laufzeiten können in jedem Thread verwendet werden, aber nur ein Thread kann jeweils einen Aufruf an eine Laufzeit vornehmen.  
  
> [!WARNING]
>  Ein JsRuntimeHandle weist im Gegensatz zu anderen Objektverweisen in der Chakra-Hosting-API keine Garbage Collection auf, da es den Heap mit Garbage Collection selbst enthält. Eine Laufzeit ist so lange vorhanden, bis JsDisposeRuntime aufgerufen wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)