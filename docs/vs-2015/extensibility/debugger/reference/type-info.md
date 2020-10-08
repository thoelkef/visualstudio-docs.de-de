---
title: TYPE_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838463"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Struktur gibt verschiedene Arten von Informationen über den Typ eines Felds an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 dwkind  
 Ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration, die bestimmt, wie die Union interpretiert werden soll.  
  
 Type. typemeta  
 [Nur C++] Enthält eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_METADATA` .  
  
 Type. typepdb  
 [Nur C++] Enthält eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_PDB` .  
  
 Type. typebuilt  
 [Nur C++] Enthält eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_BUILT` .  
  
 Type. nicht verwendet  
 Nicht verwendete Auffüll Zeichen.  
  
 type  
 Der Name der Union.  
  
 Unionmember  
 [Nur c#] Mars Hallen dieses in den entsprechenden Strukturtyp, der auf basiert `dwKind` .  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird an die [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) -Methode übermittelt, wo Sie ausgefüllt ist. Die Art und Weise, wie der Inhalt der-Struktur interpretiert wird, basiert auf dem- `dwKind` Feld.  
  
> [!NOTE]
> [Nur C++] Wenn `dwKind` `TYPE_KIND_BUILT` ist, muss beim zerstören der Struktur das zugrunde liegende [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt freigegeben werden `TYPE_INFO` . Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()` aufgerufen.  
  
 [Nur c#] In der folgenden Tabelle wird gezeigt, wie der `unionmember` Member für jede Art von Typ interpretiert wird. Das Beispiel zeigt, wie dies für eine Art von Typ erfolgt.  
  
|`dwKind`|`unionmember` interpretiert als|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie der- `unionmember` Member der- `TYPE_INFO` Struktur in c# interpretiert wird. In diesem Beispiel wird nur ein Typ ( `TYPE_KIND_METADATA` ) interpretiert, die anderen werden jedoch auf die gleiche Weise interpretiert.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
