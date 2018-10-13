---
title: IDebugMemoryContext2::GetName | Microsoft-Dokumentation
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
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e61e0a075b414d09b7e5510bd18440a5e7b4dfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299246"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Benutzer angezeigten Namen für diesen Kontext ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 [out] Gibt den Namen des Kontexts Arbeitsspeicher.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Name eines Kontexts Speicher wird normalerweise nicht verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

