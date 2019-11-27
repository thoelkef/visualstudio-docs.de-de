---
title: 'Idebugapplication:: addstackframesniffer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575030"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Fügt dieser Anwendung einen Stapel Rahmen-enumeratoranbieter hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdsfs`  
 in Der Stapel Rahmen-enumeratoranbieter, der dieser Anwendung hinzugefügt werden soll.  
  
 `pdwCookie`  
 vorgenommen Ein Cookie, das verwendet wird, um diesen Stapel Rahmen-enumeratoranbieter aus der Anwendung zu entfernen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Obwohl Sprachmodule diese Methode in der Regel zum verfügbar machen ihrer Stapel Rahmen für den Debugger aufruft, ist es möglich, dass andere Entitäten Stapel Rahmen verfügbar machen.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)