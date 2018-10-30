---
title: IDebugModule3::SetJustMyCodeState | Microsoft-Dokumentation
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
- IDebugModule3::SetJustMyCodeState
helpviewer_keywords:
- IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e7b5a9b7e0f5bcefed4e8aa3b30968140f52d2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924434"
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Markiert das Modul als Benutzercode oder nicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fIsUserCode`  
 [in] Ungleich Null (`TRUE`), wenn das Modul als Benutzercode angesehen werden sollte, NULL (`FALSE`) Wenn nicht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

