---
title: IDebugBinder3::FindAlias | Microsoft-Dokumentation
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
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18143522741abb1aebf0569db6ab1387ccd1fc02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722866"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode sucht einen Alias, erhält einen Namen an. Alle Aliase Suchen in der Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcstrName`  
 [in] Der Name des Alias gefunden.  
  
 `ppAlias`  
 [out] Alias gefunden (sofern vorhanden) dargestellt, durch die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` (wenn der Alias nicht gefunden wird) oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initialisiert das Zielobjekt, vor dem Aufruf null; testet dann null-Werte anschließend, um zu bestimmen, und zwar unabhängig davon, ob der Alias gefunden wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

