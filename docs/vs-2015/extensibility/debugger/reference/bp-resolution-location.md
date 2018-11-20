---
title: BP_RESOLUTION_LOCATION | Microsoft-Dokumentation
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
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc70710ea0a811b75e6bad3098fbbc46dae0bd3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760759"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Struktur der Haltepunktposition Auflösung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Member  
 `bpType`  
 Ein Wert aus der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Enumeration, der angibt, wie zum Interpretieren der `bpResLocation` Union oder `unionmemberX` Member.  
  
 `bpResLocation.bpresCode`  
 [Nur für C++] Enthält die [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Struktur, wenn `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [Nur für C++] Enthält die [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Struktur, wenn `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [Nur für C++] Ein Platzhalter.  
  
 `unionmember1`  
 [C# nur] Siehe Hinweise zum interpretieren.  
  
 `unionmember2`  
 [C# nur] Siehe Hinweise zum interpretieren.  
  
 `unionmember3`  
 [C# nur] Siehe Hinweise zum interpretieren.  
  
 `unionmember4`  
 [C# nur] Siehe Hinweise zum interpretieren.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) und [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Strukturen.  
  
 [C# nur] Die `unionmemberX` Elemente werden gemäß der folgenden Tabelle interpretiert. Suchen Sie in der linken Spalte für die `bpType` Wert über dann um zu bestimmen, was von den einzelnen `unionmemberX` Member darstellt und Marshal-Argument der `unionmemberX` entsprechend. Siehe das Beispiel für eine Methode zur Interpretation dieser Struktur in C# geschrieben.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (Data-Ausdruck)|`string` (Funktionsnamen)|`string` (ImageName)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie zum Interpretieren der `BP_RESOLUTION_LOCATION` Struktur in C# geschrieben.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)

