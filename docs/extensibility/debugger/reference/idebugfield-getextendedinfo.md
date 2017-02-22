---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
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
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo-Methode"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft erweiterte Informationen über ein Feld ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### Parameter  
 `guidExtendedInfo`  
 \[in\]  Wählt die Informationen aus der zurückgegeben werden soll.  Gültige Werte sind:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`guidConstantValue`|Der Wert als Bytesequenz.|  
|`guidConstantType`|Der Typ als Typsignatur.|  
  
 `prgBuffer`  
 \[out\]  Gibt die erweiterten Informationen zurück.  
  
 `pdwLen`  
 \[in, out\]  Gibt die Größe der erweiterten Informationen in Bytes zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Derzeit gibt diese Methode nur den Typ oder den Wert einer Konstante zurück.  Der Aufrufer muss den Puffer austauschen, der in `prgBuffer` zurückgegeben wird, indem `CoTaskMemFree`\-Funktion COM \(C\+\+\) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(C\#\) aufruft.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)