---
title: IJsDebugFrame-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame-Schnittstelle
Stellt einen Stapelrahmen dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Mitglieder  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate-Methode](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.|  
|[IJsDebugFrame::GetDebugProperty-Methode](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Gibt einen Eigenschaftenbrowser für diesen Stapelrahmen zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithId-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithName-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetName-Methode](../../winscript/reference/ijsdebugframe-getname-method.md)|Ruft den benutzerfreundlichen Namen des Stapelrahmens ab.|  
|[IJsDebugFrame::GetReturnAddress-Methode](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ruft die Rückgabeadresse ab, die beim "Start" des Frames mit "Push" übertragen wird (siehe GetStackRange).|  
|[IJsDebugFrame::GetStackRange-Methode](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Gibt den Bereich der absoluten Adresse des logischen JavaScript-Stapelrahmens zurück.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)