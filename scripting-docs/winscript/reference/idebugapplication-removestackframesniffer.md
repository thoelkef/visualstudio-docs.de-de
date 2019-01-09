---
title: IDebugApplication::RemoveStackFrameSniffer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46b46c8ba2cd4e87492c5cc23330baf0da27ef41
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087918"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Entfernt einen Stack-Frame-Enumerator-Anbieter von dieser Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCookie`  
 [in] Die vom zurückgegebene Cookie für die `AddStackFrameSniffer` Methode, wenn der Stack-Frame-Enumerator-Anbieter hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `RemoveStackFrameSniffer` Methode entfernt einen Stack-Frame-Enumerator-Anbieter von dieser Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)