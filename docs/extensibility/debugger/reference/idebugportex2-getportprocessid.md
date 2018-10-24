---
title: IDebugPortEx2::GetPortProcessId | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40135e1b6f9eee192dfa35ac7cae6a80a693f840
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818964"
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