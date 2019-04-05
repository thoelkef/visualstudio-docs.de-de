---
title: IDebugProgramHost2::GetHostName | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961863"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
