---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad6b7ffde868bf6b9dc4f9ef3bab9d9094ab765
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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