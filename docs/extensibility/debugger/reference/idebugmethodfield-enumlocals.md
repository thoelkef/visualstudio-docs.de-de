---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8379407a275fa4b89b4107037b2a39691d062dd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Erstellt einen Enumerator für die ausgewählten lokalen Variablen der Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in] Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt, das die Debug-Adresse, die den Kontext oder Gültigkeitsbereich aus dem Abrufen der "lokal" auswählt darstellt.  
  
 `ppLocals`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das eine Liste der lokal darstellt; andernfalls wird einen null-Wert zurückgegeben, wenn es keine "lokal sind".  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn es keine "lokal sind". Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es werden nur die Variablen, die innerhalb des Blocks mit der angegebenen Adresse definiert aufgelistet. Wenn alle "lokal", einschließlich alle vom Compiler generierte "lokal" erforderlich sind, rufen Sie die [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) Methode.  
  
 Eine Methode kann mehrere Bereichsdefinition Kontexten oder Blöcke enthalten. Beispielsweise enthält die folgenden erfundene Methode drei Bereiche, die zwei inneren Blöcke und Methodentext selbst.  
  
```csharp  
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
  
 Die [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt stellt die `func` Methode selbst. Aufrufen der `EnumLocals` Methode mit einer [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) legen Sie auf der `Inner Scope 1` Adresse zurückgibt, eine Enumeration mit der `temp1` -Variable verwenden, z. B.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)