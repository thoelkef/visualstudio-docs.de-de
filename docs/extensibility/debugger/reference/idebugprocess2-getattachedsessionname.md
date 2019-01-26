---
title: IDebugProcess2::GetAttachedSessionName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f095d72e3e008da734eb60c2193a3003624e51a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966477"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ruft den Namen der Sitzung, die diesen Prozess zu Debuggen ist. Eine IDE kann diese Informationen für einen Benutzer anzeigen, die einen bestimmten Prozess auf einem bestimmten Computer Debuggen ist.  
  
> [!NOTE]
>  Diese Methode ist veraltet, und die Implementierung sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Methode sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)