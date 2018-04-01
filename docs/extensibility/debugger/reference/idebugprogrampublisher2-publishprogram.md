---
title: IDebugProgramPublisher2::PublishProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5a76a8eb0eccad42fdd491a6efa92ad1fd5f83ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Diese Methode wird ein Programm für Debugmodule (DEs) verfügbar und die Sitzungs-Debug-Manager.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `Engines`  
 [in] Ein Array von GUIDs für DEs, die für dieses einzelne Programm anfügen bzw. starten.  
  
 `szFriendlyName`  
 [in] Anzeigename für das Programm (Dies wird in Menüs oder Dialogfeldern, die dem Benutzer angezeigt).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` Schnittstelle für das Programm (dieser Wert wird als Cookie verwendet, um die Anwendung eindeutig zu identifizieren; diese derselbe Wert wird verwendet "Veröffentlichung des Programms")  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um ein Programm nicht mehr für das Debuggen verfügbar zu machen, rufen [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)