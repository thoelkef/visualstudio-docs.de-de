---
title: IDebugArrayObject::GetRank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c6e20efe88e056b7cb780561ee2f1c3d5b057bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738844"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Rang des Arrays, d. h. die Anzahl der Dimensionen ab.  
  
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
 [out] Gibt den Rang zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) Methode, um die Größe der einzelnen Dimensionen des Array-Objekt abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

