---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ea773179232115938657f8ccc1ee1accd525f87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841472"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Erstellt eine Instanz von einer Debug-Engine auf dem Server.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szDll`  
 [in] Pfad zur Dll, die in angegebene CLSID implementiert die `clsidObject` Parameter. Ist dies `NULL`, klicken Sie dann COM `CoCreateInstance` -Funktion aufgerufen wird.  
  
 `wLangId`  
 [in] Gebietsschema der Debug-Engine. Dies kann 0 sein, wenn die [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) -Methode nicht aufgerufen werden soll.  
  
 `clsidObject`  
 [in] Die CLSID der Debug-Engine zu erstellen.  
  
 `riid`  
 [in] Schnittstellen-ID der Schnittstelle aus dem Klassenobjekt abrufen.  
  
 `ppvObject`  
 [out] `IUnknown` Schnittstelle aus dem instanziierten Objekt. Wandeln Sie aus, oder Marshallen Sie dieses Objekt auf die gewünschte Schnittstelle zu.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)