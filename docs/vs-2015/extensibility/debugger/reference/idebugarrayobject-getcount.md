---
title: 'Idebugarrayobject:: GetCount | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35cce37afc389501386ffec7b75b934e7933bc98
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68197790"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl der Elemente im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwElements`  
 vorgenommen Gibt die Anzahl zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sieht alle Elemente eines Array Objekts als eindimensionales Array, auch wenn das Array Objekt mehrdimensional ist. Bei Angabe des Arrays `myarray[3][2][6]`würde diese Methode z. b. 36 `pdwElements` im-Parameter zurückgeben. Verwenden Sie die [getElements](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) -Methode, um die einzelnen Elemente nacheinander abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
