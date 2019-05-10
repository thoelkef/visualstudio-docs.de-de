---
title: IJsDebugFrame-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57f5a848967148705a2b8dcd3f6b75dcb3a5db26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558002"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame-Schnittstelle
Stellt einen Stapelrahmen dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
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