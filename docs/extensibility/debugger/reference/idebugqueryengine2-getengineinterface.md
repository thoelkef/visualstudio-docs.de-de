---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 598606c6360993e664eda19e30b1a8b017a59e3a
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ruft eine benutzerdefinierte Debug-Modul (DE)-Schnittstelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUnk`  
 [out] Gibt eine `IUnknown` Objekt darstellt, das Debugging-Modul (DE), und der andere mit einer bereitgestellten Kompatibilitätsrichtlinie verknüpft sind und gültige Schnittstelle abgefragt werden können (z. B. [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oder [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die resultierende Schnittstelle sollte mit großer Sorgfalt verwendet werden, da-Aufruf über Schnittstellen, die von dieser Methode abgerufen der Sitzung Debug-Manager die Verarbeitung der Verwaltungsaufwand verringert, und möglicherweise die SDM in einem fehlerhaften Zustand abrufen oder Generieren von Fehlern während des Debuggens.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
