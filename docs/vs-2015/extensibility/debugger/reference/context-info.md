---
title: CONTEXT_INFO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a915458c00e75f6acb62434e184170420d15aad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524257"
---
# <a name="contextinfo"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CONTEXT_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/context-info).  
  
Diese Struktur beschreibt einen Speicherkontext oder Codekontext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Member  
 dwFields  
 Eine Kombination von Flags aus der er [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Enumeration, der angibt, welche Felder ausgefüllt sind **.**  
  
 bstrModuleUrl  
 Der Name des Moduls auf dem sich der Kontext befindet.  
  
 bstrFunction  
 Der Funktionsname, die auf dem sich der Kontext befindet.  
  
 posFunctionOffset  
 Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die den Zeile und Spalte Offset von der Funktion, die dem Codekontext zugeordnete bezeichnet.  
  
 bstrAddress  
 Die Adresse im Code, der der angegebene Kontext zugeordnet ist.  
  
 bstrAddressOffset  
 Der Offset der Adresse im Code, der der angegebene Kontext zugeordnet ist.  
  
 bstrAddressAbsolute  
 Die absolute Adresse im Speicher, in der angegebene Kontext befindet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, von einem Aufruf der [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) Methode.  
  
 Eine typische Verwendung für diese Struktur ist, Unterstützung des eine **Arbeitsspeicher** Debug-Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

