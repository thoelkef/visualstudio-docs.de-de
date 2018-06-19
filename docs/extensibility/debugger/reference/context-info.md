---
title: CONTEXT_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb634f59a3a7eb3b37e70dd87f48b22a07251d0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100431"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Diese Struktur wird eine Arbeitsspeicher-Kontext oder die Codekontext beschrieben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Eine Kombination aus Flags aus er [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) -Enumeration, der angibt, welche Felder ausgefüllt sind **.**  
  
 bstrModuleUrl  
 Der Name des Moduls, in dem Kontext befindet.  
  
 bstrFunction  
 Der Funktionsname, wo sich der Kontext befindet.  
  
 posFunctionOffset  
 Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die die Zeilen- und Spaltennummer Offset der Funktion mit dem Codekontext verknüpften bezeichnet.  
  
 bstrAddress  
 Die Adresse im Code, in dem angegebene Kontext befindet.  
  
 bstrAddressOffset  
 Der Offset der Adresse im Code, in dem angegebene Kontext befindet.  
  
 bstrAddressAbsolute  
 Die absolute Adresse im Speicher, auf dem angegebene Kontext befindet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, von einem Aufruf der [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) Methode.  
  
 Eine typische Verwendung für diese Struktur ist, unterstützen einen **Arbeitsspeicher** Debug-Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)