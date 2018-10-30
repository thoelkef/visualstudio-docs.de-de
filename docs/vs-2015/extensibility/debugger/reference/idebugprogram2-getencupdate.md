---
title: IDebugProgram2::GetENCUpdate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ca2f4fa5ff6023202a2dd038cf521ab208bfeaf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873057"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft das Update bearbeiten und Fortfahren "(ENC) für dieses Programm an. Eine benutzerdefinierten Debug-Engine gibt immer `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUpdate`  
 [out] Gibt eine interne Schnittstelle, die zum Aktualisieren dieses Programms verwendet werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Eine benutzerdefinierten Debug-Engine sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

