---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "TYPE_INFO-Struktur"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur gibt verschiedene Arten von Informationen über einen Feldtyp an.  
  
## Syntax  
  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### Parameter  
 dwKind  
 Ein Wert aus der Enumeration [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) , durch die bestimmt wird, wie die Gesamtmenge interpretiert.  
  
 type.typeMeta  
 \[C\+\+\] Es enthält eine [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Struktur, wenn `dwKind``TYPE_KIND_METADATA`ist.  
  
 type.typePdb  
 \[C\+\+\] Es enthält eine [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Struktur, wenn `dwKind``TYPE_KIND_PDB`ist.  
  
 type.typeBuilt  
 \[C\+\+\] Es enthält eine [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) Struktur, wenn `dwKind``TYPE_KIND_BUILT`ist.  
  
 type.unused  
 Nicht verwendete Auffüllung.  
  
 type  
 Name der Union.  
  
 unionmember  
 \[C\#\] nur in den richtigen Marshallen dieses Strukturtyp auf Grundlage `dwKind`.  
  
## Hinweise  
 Diese Struktur wird auf die [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)\-Methode übergeben, in der er eingetragen wird.  Wie die Inhalte der Struktur interpretiert werden, basiert auf dem `dwKind` Feld.  
  
> [!NOTE]
>  \[C\+\+\] Es `dwKind` wenn `TYPE_KIND_BUILT`entspricht, dann muss das zugrunde liegende [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt freigibt, wenn die `TYPE_INFO` Struktur gelöscht.  Hierzu wird `typeInfo.type.typeBuilt.pUnderlyingField->Release()`aufruft.  
  
 \[C\#\] zeigt nur die folgende Tabelle veranschaulicht, wie der `unionmember`\-Member für jede Art von Typ interpretiert.  Im Beispiel wird gezeigt, wie dies für eine Art von Typ.  
  
|`dwKind`|`unionmember` wie interpretierte|  
|--------------|--------------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## Beispiel  
 Dieses Beispiel zeigt, wie der `unionmember`\-Member der `TYPE_INFO` Struktur in C\# interpretiert.  In diesem Beispiel wird das Interpretieren von nur einem Typ \(`TYPE_KIND_METADATA`\), aber die anderen werden auf die gleiche Art interpretiert genau.  
  
```c#  
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
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)