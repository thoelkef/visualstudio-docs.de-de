---
title: 'IDebugEngine2:: abtregistryroot | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39bb532301d34a3abf9988cfa909e1606c3c73e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195943"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Registrierungs Stamm für die Debug-Engine (de) fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszRegistryRoot`  
 in Der zu verwendende Registrierungs Stamm.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ermöglicht das [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Angeben eines alternativen Registrierungs Stamms, das von der de zum Abrufen von Registrierungs Einstellungen verwendet werden soll, z. b. "HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp".  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
