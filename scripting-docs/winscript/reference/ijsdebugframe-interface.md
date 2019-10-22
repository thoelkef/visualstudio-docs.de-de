---
title: Ijsdebugframe-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575105"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame-Schnittstelle
Stellt einen Stapelrahmen dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|-Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate-Methode](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.|  
|[IJsDebugFrame::GetDebugProperty-Methode](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Gibt einen Eigenschaftenbrowser für diesen Stapelrahmen zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithId-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithName-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetName-Methode](../../winscript/reference/ijsdebugframe-getname-method.md)|Ruft den benutzerfreundlichen Namen des Stapelrahmens ab.|  
|[IJsDebugFrame::GetReturnAddress-Methode](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ruft die Rückgabeadresse ab, die beim "Start" des Frames mit "Push" übertragen wird (siehe GetStackRange).|  
|[IJsDebugFrame::GetStackRange-Methode](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Gibt den Bereich der absoluten Adresse des logischen JavaScript-Stapelrahmens zurück.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)