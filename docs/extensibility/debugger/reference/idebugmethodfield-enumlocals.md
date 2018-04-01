---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 451c2ccad7d817946bd3d2c2e83ed27279124f2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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