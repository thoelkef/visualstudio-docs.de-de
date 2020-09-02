---
title: 'Idebugprocesssecurity:: querycansafelyattach | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187961"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Mit dieser Methode kann der Port Lieferant eine Warnung anzeigen, bevor der Benutzer an einen unsicheren Prozess angefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die Rückgabewerte lauten wie folgt:  
  
- `S_OK`: Das Anhängen an den Prozess ist sicher, und es wird kein Warn Dialogfeld angezeigt.  
  
- `S_FALSE`: Das Anfügen kann ein Sicherheitsproblem sein, und es wird ein Dialogfeld mit einer Warnung angezeigt.  
  
- `FAILURE`: Fehler beim Anhängen an den Prozess.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
