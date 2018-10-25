---
title: IDebugProgramNode2::GetEngineInfo | Microsoft-Dokumentation
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
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89feb9dfb39b87be282ececde446dfc80e6da202
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934053"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen und Bezeichner des Debug-Engine (DE) ein Programm ausgeführt wird.  
  
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
 [out] Gibt den Namen der Ausführung des Programms DE zurück (C++-spezifischen: Dies kann ein null-Zeiger, der angibt, dass der Aufrufer nicht den Namen der Engine interessiert sein).  
  
 `pguidEngine`  
 [out] Gibt den globally unique Identifier des DE Ausführung des Programms (C++-spezifischen: Dies kann ein null-Zeiger, der angibt, dass der Aufrufer nicht der GUID des Moduls interessiert sein).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

