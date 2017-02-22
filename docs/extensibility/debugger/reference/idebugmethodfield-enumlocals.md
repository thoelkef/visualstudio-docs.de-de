---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
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
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals-Methode"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.  
  
## Syntax  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt, das die Debuginformationen Adresse darstellt, die den Kontext und den Gültigkeitsbereich auswählt, von denen die lokalen Variablen abrufen.  
  
 `ppLocals`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das eine Liste der lokalen Variablen darstellt. Andernfalls gibt einen NULL\-Wert zurück, wenn keine lokalen Variablen vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine lokalen Variablen vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nur die Variablen, die innerhalb des Blocks definiert werden, die mit der angegebenen Adresse, werden aufgezählt.  Wenn alle lokalen Variablen, einschließlich aller vom Compiler generierten lokalen Variablen erforderlich sind, rufen Sie die [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)\-Methode auf.  
  
 Eine Methode kann die mehrere Kontexte oder Blöcke enthalten.  Beispielsweise enthält die folgende fiktive Methode drei Bereiche, die zwei inneren Blöcke und den Methodentext selbst.  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 Das [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)\-Objekt stellt die `func`\-Methode selbst dar.  Die `EnumLocals`\-Methode mit [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) das Aufrufen der `Inner Scope 1` Adresse festgelegt ist, gibt eine Enumeration zurück, die die Variable `temp1` beispielsweise enthält.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)