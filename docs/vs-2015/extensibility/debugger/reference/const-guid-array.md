---
title: CONST_GUID_ARRAY | Microsoft-Dokumentation
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
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af527759568d2f36d120002e7216e1d6ce517b54
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816741"
---
# <a name="constguidarray"></a>CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Eine Struktur, die eine Liste der enthält `GUID`s.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```csharp  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## <a name="members"></a>Member  
 dwCount  
 Anzahl der `GUID`s in der `Members` Array.  
  
 Member  
 Array von `GUID`s.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) -Methode und wird zurückgegeben, aus der [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) und [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) Methoden.  
  
 Der Besitzer einer Instanz dieser Struktur ist verantwortlich für das Freigeben von Speicher.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

