---
title: BP_RESOLUTION_LOCATION | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ea6539f2ed790dda5cc4c9de126aa226f4b2686
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153290"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Struktur der Haltepunkt Auflösung an.  
  
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
 Ein Wert aus der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) -Enumeration, der angibt, wie die Union oder Member interpretiert werden sollen `bpResLocation` `unionmemberX` .  
  
 `bpResLocation.bpresCode`  
 [Nur C++] Enthält die [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Struktur, wenn `bpType`  =  `BPT_CODE` .  
  
 `bpResLocation.bpresData`  
 [Nur C++] Enthält die [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Struktur, wenn `bpType`  =  `BPT_DATA` .  
  
 `bpResLocation.unused`  
 [Nur C++] Ein Platzhalter.  
  
 `unionmember1`  
 [Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.  
  
 `unionmember2`  
 [Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.  
  
 `unionmember3`  
 [Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.  
  
 `unionmember4`  
 [Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur ist ein Member der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) -und [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) -Strukturen.  
  
 [Nur c#] Die Elemente `unionmemberX` werden entsprechend der folgenden Tabelle interpretiert. Suchen Sie in der linken Spalte nach dem `bpType` Wert, und wählen Sie dann aus, um zu bestimmen, was die einzelnen Elemente `unionmemberX` darstellen und wie Sie die `unionmemberX` Im Beispiel finden Sie eine Möglichkeit zum Interpretieren dieser Struktur in c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (Daten Ausdruck)|`string` (Funktionsname)|`string` (Bildname)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie die- `BP_RESOLUTION_LOCATION` Struktur in c# interpretiert wird.  
  
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
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
