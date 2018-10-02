---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 243c8556e38bd89200ca591d4b087e441baf57f1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524389"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProcessSecurity::QueryCanSafelyAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach).  
  
Diese Methode ermöglicht Anschlusslieferanten um eine Warnung anzuzeigen, bevor der Benutzer fügt eine unsichere Prozess an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die Rückgabewerte sind wie folgt aus:  
  
-   `S_OK`: Das Anfügen an Prozess sicher ist und kein Warnungsdialogfeld wird angezeigt.  
  
-   `S_FALSE`: Anfügen ist möglicherweise ein Sicherheitsproblem vor, und ein Dialogfeld mit einer Warnung angezeigt wird.  
  
-   `FAILURE`: Das Anhängen an Prozess ein Fehler auftritt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

