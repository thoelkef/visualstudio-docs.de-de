---
title: IDebugModuleLoadEvent2::GetModule | Microsoft-Dokumentation
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
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 614fceea8b2ca2e5198b4a748c430d804cde7442
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179843"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Modul, das gerade geladen oder entladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pModule`  
 [out] Gibt eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt, das das Modul darstellt, die geladen oder entladen wird.  
  
 `pbstrDebugMessage`  
 [in, out] Gibt eine optionale Nachricht, die dieses Ereignis beschreibt. Wenn dieser Parameter ein null-Wert ist, wird keine Meldung angefordert.  
  
 `pbLoad`  
 [in, out] Ungleich Null (`TRUE`) Wenn das Modul geladen und 0 (null) ist (`FALSE`), wenn das Modul entladen wird. Wenn dieser Parameter ein null-Wert ist, wird kein Status angefordert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)

