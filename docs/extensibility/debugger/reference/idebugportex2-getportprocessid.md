---
title: IDebugPortEx2::GetPortProcessId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a9cb6a85cd23f0859c8f9ce0aff8c9ef21bf80
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941755"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ruft die Prozess-ID des Ports selbst ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwProcessId`  
 [out] Gibt die physischen Prozess-ID des Ports selbst zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Win32-Runtime ruft z. B. diese Methode in der Regel die Win32-Funktion `GetCurrentProcessId` Abrufen die physischen Prozess-ID.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)