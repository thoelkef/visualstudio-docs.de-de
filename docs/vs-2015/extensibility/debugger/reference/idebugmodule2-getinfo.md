---
title: 'IDebugModule2:: GetInfo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 476ffb2901dfe6a8d09ca707fc47089f4d99d97d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162496"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft Informationen zu diesem Modul ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 in Eine Kombination von Flags aus der [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Enumeration, die angeben, welche Felder von `pInfo` ausgefüllt werden sollen.  
  
 `pInfo`  
 [in, out] Eine [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) -Struktur, die mit einer Beschreibung des Moduls ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) -Struktur enthält den Namen des Moduls, das im Fenster " **Module** " angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
