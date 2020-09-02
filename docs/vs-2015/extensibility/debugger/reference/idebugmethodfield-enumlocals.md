---
title: 'Idebugmethodfield:: enumlocals | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2306bbf0c44a883c584346c3dbb3dd70e9b39175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162600"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Ein [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das die debugadresse darstellt, mit der der Kontext oder der Gültigkeitsbereich für die lokalen Variablen ausgewählt wird.  
  
 `ppLocals`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das eine Liste der lokalen Variablen darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, wenn keine lokalen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine lokalen vorhanden sind Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Nur die Variablen, die in dem Block definiert sind, der die angegebene debugadresse enthält, werden aufgezählt. Wenn alle lokalen Variablen, einschließlich der vom Compiler generierten lokalen Variablen, benötigt werden, müssen Sie die [enumalllocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) -Methode aufrufen.  
  
 Eine Methode kann mehrere Bereichs bezogene Kontexte oder Blöcke enthalten. Beispielsweise enthält die folgende erfunderte Methode drei Bereiche, die beiden inneren Blöcke und den Methoden Text selbst.  
  
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
  
 Das [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt stellt die `func` Methode selbst dar. Das Aufrufen der- `EnumLocals` Methode mit einer [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) , die auf die Adresse festgelegt `Inner Scope 1` ist, gibt eine Enumeration zurück, die die `temp1` Variable enthält, z.b..  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
