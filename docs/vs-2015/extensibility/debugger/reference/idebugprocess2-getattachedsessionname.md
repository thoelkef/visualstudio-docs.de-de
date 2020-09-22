---
title: 'IDebugProcess2:: getattachedsessionname | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3acc40e2b906bd46b832d9fa11578de346014042
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840896"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen der Sitzung ab, die diesen Prozess debuggt. Eine IDE kann diese Informationen für einen Benutzer anzeigen, der einen bestimmten Prozess auf einem bestimmten Computer debuggt.  
  
> [!NOTE]
> Diese Methode ist veraltet, und ihre Implementierung sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Methode sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
