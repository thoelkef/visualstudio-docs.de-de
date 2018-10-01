---
title: IDebugEngine2::GetEngineID | Microsoft-Dokumentation
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
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0326f165b31ab2597b01561fc2b86854eda04c61
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523388"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugEngine2::GetEngineID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-getengineid).  
  
Ruft die GUID der Debug-Engine (DE) ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pguidEngine`  
 [out] Gibt die GUID des DE zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Einige Beispiele für typische GUIDs sind `guidScriptEng`, `guidNativeEng`, oder `guidSQLEng`. Neue Debug-Engines erstellt eigene GUID zur Identifikation.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CEngine` Objekt, das implementiert die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle.  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

