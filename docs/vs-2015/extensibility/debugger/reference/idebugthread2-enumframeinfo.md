---
title: 'IDebugThread2:: enumframeinfo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efda31daae198befbda35803ef71e1d0322e9bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153083"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste der Stapel Rahmen für diesen Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFieldSpec`  
 in Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, die angibt, welche Felder der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen ausgefüllt werden sollen. Geben `FIF_FUNCNAME_FORMAT` Sie das Flag an, um den Funktionsnamen in einer einzelnen Zeichenfolge zu formatieren.  
  
 `nRadix`  
 in Der zum Formatieren von numerischen Informationen im Enumerator verwendete Radix.  
  
 `ppEnum`  
 vorgenommen Gibt ein [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Objekt zurück, das eine Liste der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen enthält, die den Stapel Rahmen beschreiben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Rahmen des Threads werden in der Reihenfolge aufgelistet, wobei der aktuelle Frame zuerst aufgezählt und der älteste enumerationsframe zuletzt aufgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
