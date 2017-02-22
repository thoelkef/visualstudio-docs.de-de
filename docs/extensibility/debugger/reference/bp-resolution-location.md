---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "BP_RESOLUTION_LOCATION-Struktur"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Struktur des Haltepunkts auflösungs speicherorts an.  
  
## Syntax  
  
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
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Mitglieder  
 `bpType`  
 Ein Wert aus der [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)\-Enumeration, die angibt, wie die `bpResLocation` Union oder `unionmemberX`\-Member interpretiert.  
  
 `bpResLocation.bpresCode`  
 \[C\+\+\] Es enthält die [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Struktur wenn `bpType` \= `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[C\+\+\] Es enthält die [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Struktur wenn `bpType` \= `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[C\+\+\] Es a\-Platzhalter.  
  
 `unionmember1`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember2`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember3`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember4`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) und [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Strukturen.  
  
 \[C\#\] `unionmemberX` nur die Member entsprechend der folgenden Tabelle interpretiert.  Suchen Sie entlang der linken Spalte auf dem `bpType`\-Wert für, um zu bestimmen, welche Member darstellt, und jeder `unionmemberX` Marshallen von `unionmemberX` .  Weitere Informationen finden Sie im Beispiel, dass eine Methode diese Struktur in C\# interpretiert.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` Daten \(Ausdruck\)|`string` \(Funktionsname\)|Bild \(Name\)`string`|`enum_BP_RES_DATA_FLAGS`|  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `BP_RESOLUTION_LOCATION` Struktur in C\# interpretiert.  
  
```c#  
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
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)