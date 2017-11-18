---
title: IEnumJsStackFrames-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames-Schnittstelle
Implementiert durch den Debugger, um zu "jscript9diag.dll" Stapelentladung für JavaScript bereitzustellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Mitglieder  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next-Methode](../../winscript/reference/ienumjsstackframes-next-method.md)|Ruft die angegebene Anzahl an Frames ab.|  
|[IEnumJsStackFrames::Reset-Methode](../../winscript/reference/ienumjsstackframes-reset-method.md)|Setzt den Stapelrahmen auf die Position vor dem ersten Element zurück.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)