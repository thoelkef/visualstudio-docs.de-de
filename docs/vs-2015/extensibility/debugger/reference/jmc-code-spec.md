---
title: JMC_CODE_SPEC | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca7d6bfb799f0a9460702c4b581ef3f5261672b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147482"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur wird verwendet, um die JustMyCode-Informationen für ein Modul festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Member  
 "fsusercode"  
 Ungleich NULL ( `TRUE` ), wenn das Modul als Benutzercode angesehen werden soll, andernfalls 0 (NULL `FALSE` ) (), wenn das Modul als externer Code behandelt werden soll und nicht deentschlgt werden soll.  
  
 bstranmodulename  
 Der Name des fraglichen Moduls.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird als Liste solcher Strukturen an die [setjustmycodestate](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) -Methode übermittelt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
