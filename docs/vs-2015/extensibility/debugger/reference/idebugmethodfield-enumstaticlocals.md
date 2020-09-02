---
title: 'Idebugmethodfield:: enumstaticlocals | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69230ce3f748cca460c08d2d40648523161707d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162583"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für statische lokale Variablen der Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppLocals`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der statischen lokalen Variablen darstellt. Gibt einen NULL-Wert zurück, wenn keine statischen lokalen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine statischen lokalen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Element ist ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das verschiedene Typen von statischen lokalen Variablen darstellt. Aufrufen der [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für jedes Objekt, um genau zu bestimmen, welche Art von statischem lokalen Objekt das Objekt darstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
