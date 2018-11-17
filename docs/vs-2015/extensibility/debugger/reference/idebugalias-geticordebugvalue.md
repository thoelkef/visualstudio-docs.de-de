---
title: IDebugAlias::GetICorDebugValue | Microsoft-Dokumentation
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
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e052a720f73ff6df3f716932dba2a1f8ea87c94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807672"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ab eine verwaltete Codeschnittstelle, die den Wert dieser Alias darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUnk`  
 [out] `IUnknown` Schnittstelle, die den Wert dieser Alias darstellt. Diese Schnittstelle abgefragt werden kann, für die `ICorDebugValue` Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gilt nur für verwaltete Werte (die `ICorDebugValue` steht eine Schnittstelle in der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] und in der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] -SDK in der Datei "cordebug.idl").  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

