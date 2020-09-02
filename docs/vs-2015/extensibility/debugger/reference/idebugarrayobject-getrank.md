---
title: 'Idebugarrayobject:: GetRank | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf9700e2c3b29561229999506ed789a2e3d6e52e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423672"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Rang des Arrays ab, d. h. die Anzahl der Dimensionen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwRank`  
 vorgenommen Gibt den Rang zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) -Methode, um die Größe der einzelnen Dimensionen des Array-Objekts abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
