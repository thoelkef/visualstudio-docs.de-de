---
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0083946051fe78fc1bd19ea877475465e0b6477f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163421"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Modul ab, das geladen oder entladen wird.  
  
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
 vorgenommen Gibt ein [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt zurück, das das Modul darstellt, das geladen oder entladen wird.  
  
 `pbstrDebugMessage`  
 [in, out] Gibt eine optionale Meldung zurück, die dieses Ereignis beschreibt. Wenn dieser Parameter ein NULL-Wert ist, wird keine Meldung angefordert.  
  
 `pbLoad`  
 [in, out] Ungleich NULL ( `TRUE` ), wenn das Modul geladen wird, und 0 (NULL `FALSE` ) (), wenn das Modul entladen wird. Wenn dieser Parameter ein NULL-Wert ist, wird kein Status angefordert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
