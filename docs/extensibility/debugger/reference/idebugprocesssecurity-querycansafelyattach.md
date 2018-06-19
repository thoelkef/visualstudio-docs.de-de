---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe132ddbd154e04e3cef1a20e826c3634c65bdb2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114228"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Diese Methode lässt den Lieferanten Port eine Warnung angezeigt, bevor der Benutzer zu einem unsicheren Prozess anfügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die Rückgabewerte sind wie folgt aus:  
  
-   `S_OK`: Das Anfügen an Prozess sicher ist, und keine Warndialogfeld angezeigt wird.  
  
-   `S_FALSE`: Anfügen konnte kein Sicherheitsproblem werden, und ein Dialogfeld mit einer Warnung angezeigt wird.  
  
-   `FAILURE`: Anfügen an Prozess ein Fehler auftritt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)