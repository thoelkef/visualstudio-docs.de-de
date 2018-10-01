---
title: IDebugObject2::IsUserData | Microsoft-Dokumentation
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
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0bb59629c3a82826d00053109d9cb5980d70630
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513937"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugObject2::IsUserData](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-isuserdata).  
  
Bestimmt, ob das Objekt mit Daten des Benutzers darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfUser`  
 [out] Ungleich NULL zurückgibt (`TRUE`) NULL, wenn das Objekt auf Benutzerdaten; darstellt (`FALSE`), wenn dies nicht der Fall.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Benutzerdaten sind ein Objekt, das Teil eines Moduls, das als JustMyCode (eine konfigurierbare Option, die ein Modul als Benutzercode und daher in eine stapelüberwachung sichtbar markiert) festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

