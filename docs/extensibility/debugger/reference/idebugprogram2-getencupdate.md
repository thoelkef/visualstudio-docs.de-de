---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetENCUpdate
helpviewer_keywords: IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d0d14d407dbff9493af0206369cfd8b9c8d556c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Diese Methode ruft das Update bearbeiten und Fortfahren (ENC) für dieses Programm an. Immer gibt einen benutzerdefinierten Debugmodul `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [out] Gibt eine interne Schnittstelle, die verwendet werden kann, um dieses Programm zu aktualisieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Einen benutzerdefinierten Debugmodul sollte stets `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)