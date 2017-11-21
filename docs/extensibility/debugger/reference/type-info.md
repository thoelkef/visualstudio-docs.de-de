---
title: TYPE_INFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TYPE_INFO
helpviewer_keywords: TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dc77aa5b633c4160fc34717c0b9382d89d9f0e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="typeinfo"></a>TYPE_INFO
Diese Struktur gibt verschiedene Arten von Informationen zum Typ des Felds an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 dwKind  
 Ein Wert aus der [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) -Enumeration, der bestimmt, wie die Union zu interpretieren.  
  
 type.typeMeta  
 [Nur C++] Enthält eine [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Nur C++] Enthält eine [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Nur C++] Enthält eine [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur, wenn `dwKind` ist `TYPE_KIND_BUILT`.  
  
 Type.Unused  
 Nicht verwendete Auffüllung.  
  
 Typ  
 Die Namen der Union.  
  
 Unionmember  
 [C#] Marshallen, die diese Option, um den entsprechenden Strukturtyp basierend auf `dwKind`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) Methode, wo in gefüllt. Die Interpretation der Inhalt der Struktur basiert auf den `dwKind` Feld.  
  
> [!NOTE]
>  [Nur C++] Wenn `dwKind` gleich `TYPE_KIND_BUILT`, ist es erforderlich, die Version des zugrunde liegenden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt beim Zerstören von der `TYPE_INFO` Struktur. Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()` aufgerufen.  
  
 [C#] Die folgende Tabelle zeigt die Interpretation der `unionmember` Member für jede Art von Typ. Im Beispiel wird gezeigt, wie dies für eine Art von Datentyp ausgeführt wird.  
  
|`dwKind`|`unionmember`interpretiert als|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie zum Interpretieren der `unionmember` Mitglied der `TYPE_INFO` Struktur in C# geschrieben. Dieses Beispiel zeigt nur einen Typ zu interpretieren (`TYPE_KIND_METADATA`) jedoch andere auf genau die gleiche Weise interpretiert werden.  
  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)