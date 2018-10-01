---
title: IDebugArrayField::GetNumberOfElements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a950580417b168796708b0924d756a580bc2b3c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513183"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugArrayField::GetNumberOfElements](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayfield-getnumberofelements).  
  
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

