---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords: IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Erstellt eine Instanz von Debugging-Modul auf dem Server.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
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
 [in] Pfad zur Dll, die die im angegebenen CLSID implementiert die `clsidObject` Parameter. Ist dies `NULL`, klicken Sie dann COM `CoCreateInstance` Funktion aufgerufen wird.  
  
 `wLangId`  
 [in] Gebietsschema der Debugging-Modul. Dies kann 0 sein, wenn die [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) Methode sollte nicht aufgerufen werden.  
  
 `clsidObject`  
 [in] Die CLSID der Debugging-Modul erstellen.  
  
 `riid`  
 [in] Schnittstellen-ID der Schnittstelle zum Abrufen von das Klassenobjekt.  
  
 `ppvObject`  
 [out] `IUnknown` Schnittstelle aus dem instanziierten Objekt. Umgewandelt oder dieses Objekt auf die gewünschte Schnittstelle zu marshallen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)