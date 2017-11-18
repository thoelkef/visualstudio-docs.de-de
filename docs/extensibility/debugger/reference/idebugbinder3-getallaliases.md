---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetAllAliases
helpviewer_keywords: IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a01c05354c6dcf80967e1b577a9adde11a7fdb7a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Diese Methode ruft eine Liste der Aliase aus der Anwendung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uRequest`  
 [in] Die maximale Anzahl der zurückzugebenden Aliase (gibt die Länge des übergebenen Arrays `ppAliases`).  
  
 `ppAliases`  
 [in, out] Mit Aliasnamen auszufüllende Array (ist dies ein null-Wert und `uRequest` gleich 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können zurückgegeben werden, indem `puFetched`).  
  
 `puFetched`  
 [out] Gibt die Anzahl von Aliasen abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)