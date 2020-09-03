---
title: 'IDebugProgramNode2:: getengineingefo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3e24c2c326f7ebc7427da3804f17f1f75aeef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205735"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen und den Bezeichner der Debug-Engine (de) ab, die ein Programm ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrEngine`  
 vorgenommen Gibt den Namen des Programms zurück, auf dem das Programm ausgeführt wird (C++-specific: Dies kann ein NULL-Zeiger sein, der angibt, dass der Aufrufer nicht an dem Namen der Engine interessiert ist).  
  
 `pguidEngine`  
 vorgenommen Gibt die Globally Unique Identifier der de zurück, die das Programm ausgeführt hat (C++-specific: Dies kann ein NULL-Zeiger sein, der angibt, dass der Aufrufer nicht an der GUID der Engine interessiert ist).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
