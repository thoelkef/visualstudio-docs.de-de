---
title: 'IDebugProcess2:: GetInfo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57944fe59bbf33f3d63a63570fcd25e25e927b6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187996"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Beschreibung des Prozesses ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `Fields`  
 in Eine Kombination von Werten aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Enumeration, die angibt, welche Felder des `pProcessInfo` Parameters ausgefüllt werden sollen.  
  
 `pProcessInfo`  
 vorgenommen Eine [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) -Struktur, die mit einer Beschreibung des Prozesses ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
