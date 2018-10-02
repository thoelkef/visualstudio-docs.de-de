---
title: IDebugProgramHost2::GetHostName | Microsoft-Dokumentation
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
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 420a25be81a124c89bc4139d80ae881b1f519726
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523170"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgramHost2::GetHostName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2-gethostname).  
  
Ruft ab, der Titel, Anzeigename oder der Dateiname des Hostprozesses dieses Programms.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwType`  
 [in] Ein Wert aus der [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Enumeration.  
  
 `pbstrHostName`  
 [out] Gibt den angeforderten Namen des Hostprozesses.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In einer typischen Implementierung dieser Methode die `dwType` Parameter wird ignoriert, und ein Benutzerfreundlicher Namen des Hostcomputers wird zurückgegeben. Eine andere mögliche Implementierung besteht darin, übergeben die `dwType` Parameter, um einen Aufruf der [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) Methode, um den Namen zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

