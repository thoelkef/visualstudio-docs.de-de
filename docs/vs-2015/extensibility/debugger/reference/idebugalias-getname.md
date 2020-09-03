---
title: 'Idebugalias:: GetName | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a52f44caa896a528557e9e2ac362c47584e47f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149343"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen dieses Alias ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 vorgenommen Der Name des Alias.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
