---
title: IDebugProcess2::GetAttachedSessionName | Microsoft-Dokumentation
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
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f974ab7e12e85ec72ebb310aded986d77e7fcb7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256138"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

