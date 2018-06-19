---
title: BUILT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14a9010925db5c175b7110fb12261eb135162246
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100363"
---
# <a name="builttype"></a>BUILT_TYPE
Diese Struktur gibt Informationen zu Metadaten entnommen Feldtyp an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 ulAppDomainID  
 Die ID der Anwendung, von der das Symbol stammt. Dient zur eindeutigen Identifizierung eine Instanz der Anwendung.  
  
 guidModule  
 Die GUID des Moduls, das dieses Feld enthält.  
  
 pUnderlyingField  
 Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das das zugrunde liegende Feld dieser erstellte Feld zugeordneten bezeichnet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Teil der Union der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strukturieren, wenn die `dwKind` -Feld der der `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_BUILT` (ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) die Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)