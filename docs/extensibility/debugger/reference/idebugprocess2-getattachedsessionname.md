---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetAttachedSessionName
helpviewer_keywords: IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8ca045a1fee17891fbe053d1d072a4affa41c787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ruft den Namen der Sitzung, die diesen Prozess zu Debuggen ist. Eine IDE kann diese Informationen für einen Benutzer angezeigt, die einen bestimmten Prozess auf einem bestimmten Computer Debuggen ist.  
  
> [!NOTE]
>  Diese Methode ist veraltet, und ihre Implementierung sollte stets `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Methode sollte stets `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)