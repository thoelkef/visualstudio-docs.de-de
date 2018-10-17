---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 5380df694196f8a0ec8fea11aefd429ccfeca039
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239329"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

