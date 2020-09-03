---
title: CONST_GUID_ARRAY | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43715ca8fa8174b2b8b9509a93e98cf15ad4611c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198861"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Eine-Struktur, die eine Liste von `GUID` s enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```csharp  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## <a name="members"></a>Member  
 dwCount  
 Anzahl von `GUID` s im `Members` Array.  
  
 Member  
 Array von `GUID` s.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird an die [publishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) -Methode übermittelt und von der [getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) -Methode und der [watchforproviderevents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) -Methode zurückgegeben.  
  
 Der Besitzer einer Instanz dieser Struktur ist dafür verantwortlich, zugeordneten Arbeitsspeicher freizugeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Publishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)   
 [Getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
