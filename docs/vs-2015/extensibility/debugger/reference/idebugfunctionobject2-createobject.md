---
title: IDebugFunctionObject2::CreateObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2053282cd37f874a7f0f1dcd7e6b31e223923fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515070"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugFunctionObject2::CreateObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionobject2-createobject).  
  
Erstellt ein Objekt, das einen Konstruktor, der angegebenen Einstellungen für die Evaluierung und einen Timeoutwert verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pConstructor`  
 [in] Ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt, das den Konstruktor des zu erstellenden-Objekts darstellt.  
  
 `dwArgs`  
 [in] Die Anzahl von Parametern in der `pArg` Array. Gibt die Anzahl von Parametern, die an den Konstruktor übergeben.  
  
 `pArgs`  
 [in] Ein Array von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte, die Parameter darstellt, die an den Konstruktor übergeben.  
  
 `dwEvalFlags`  
 [in] Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung ausgeführt werden.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung **UNENDLICHE** für Warten ohne Timeout.  
  
 `ppObject`  
 [out] Gibt eine **IDebugObject** , das das neu erstellte Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode, um ein Objekt zu erstellen, die eine Instanz einer Klasse oder anderen komplexen Typs, der einen Konstruktor erforderlich sind, die einen Parameter darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

