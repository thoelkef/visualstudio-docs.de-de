---
title: IDebugProgram2::GetENCUpdate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 5b06716c2a9de2e2fb61a372c51f2f574065aefc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523597"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgram2::GetENCUpdate](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getencupdate).  
  
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

