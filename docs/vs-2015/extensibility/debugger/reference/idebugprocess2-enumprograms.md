---
title: 'IDebugProcess2:: enumprograms | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumPrograms
helpviewer_keywords:
- IDebugProcess2::EnumPrograms
ms.assetid: f5b7295d-487d-464f-a4c6-d54175b07705
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8391bdd01d33a39810ed45f56cd064e76464153e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188033"
---
# <a name="idebugprocess2enumprograms"></a>IDebugProcess2::EnumPrograms
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste aller Programme ab, die in diesem Prozess enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```csharp  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) -Objekt zurück, das eine Liste aller Programme im Prozess enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
