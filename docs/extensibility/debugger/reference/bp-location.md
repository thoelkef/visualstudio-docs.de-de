---
title: "BP_LOCATION | Microsoft Docs"
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
  - "BP_LOCATION"
helpviewer_keywords: 
  - "BP_LOCATION union"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Typ der Struktur verwendet, um die Position des Haltepunkts zu beschreiben.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## Mitglieder  
 `bpLocationType`  
 Ein Wert aus der [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)\-Enumeration verwendet, um die `bpLocation` Union oder `unionmemberX`\-Member zu interpretieren.  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur wenn `bpLocationType` \= `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur wenn `bpLocationType` \= `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Struktur wenn `bpLocationType` \= `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Struktur wenn `bpLocationType` \= `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Struktur wenn `bpLocationType` \= `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Struktur wenn `bpLocationType` \= `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 \[C\+\+\] Es enthält die [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Struktur wenn `bpLocationType` \= `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember2`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember3`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
 `unionmember4`  
 \[Nur C\#\] siehe Hinweise zur Verwendung interpretiert.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
 \[C\#\] `unionmemberX` nur die Member entsprechend der folgenden Tabelle interpretiert.  Suchen Sie nach dem entlang der linken Spalte `bpLocationType`\-Wert finden Sie über den anderen Spalten, um zu bestimmen, welche Member darstellt, und jeder `unionmemberX` Marshallen von `unionmemberX` .  Weitere Informationen finden Sie im Beispiel, dass eine Methode einen Teil dieser Struktur in C\# interpretiert.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(Kontext\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(Kontext\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(Kontext\)|`string` \(bedingter Ausdruck\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(Kontext\)|`string` Modul \(URLs\)|`string` \(Funktionsname\)|`string` \(Adresse\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(Kontext\)|`string` Daten \(Ausdruck\)|`uint` \(Anzahl der Elemente\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `BP_LOCATION` Struktur in C\# für den `BPLT_DATA_STRING`\-Typ interpretiert.  Der spezifische Typ wird gezeigt, wie alle vier `unionmemberX`\-Member in allen Formaten interpretiert, Zeichenfolgen\- und \- Objekt \(Zahl\).  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
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
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)