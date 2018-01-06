---
title: IDebugEngine3::LoadSymbols | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97509031e123babf5febfd51ebff3047e5d21ccf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Lädt (nach Bedarf)-Symbole für alle Module, die von diesem Debugmodul gedebuggt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Dadurch wird die Debugsymbole für alle Module auf diesem Debugmodul verweist geladen. Die Symbole geladen sind, nur dann, wenn sie noch nicht geladen wurden. Symbole werden durchsucht, auf die Pfade durch einen Aufruf von [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)