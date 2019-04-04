---
title: IDebugArrayField::GetNumberOfElements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5627f263d743c4f8c83de683c24baf21cf594a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958648"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl der Elemente im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwNumElements`  
 [out] Gibt die Anzahl der Elemente im Array zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der zurückgegebene Wert ist die Gesamtanzahl der Elemente im Array, unabhängig von der Anzahl von Dimensionen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
