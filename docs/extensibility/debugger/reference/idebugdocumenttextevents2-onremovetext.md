---
title: IDebugDocumentTextEvents2::onRemoveText | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 99c7313374b5e0eb89ff578c0df12635b01f3dff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849416"
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
Benachrichtigt dem debugpaket an, dass Text aus dem Dokument entfernt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT onRemoveText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToRemove  
);  
```  
  
```csharp  
int onRemoveText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToRemove  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pos`  
 [in] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die angibt, in dem der Text entfernt wurde.  
  
 `dwNumToRemove`  
 [in] Gibt die Anzahl der Zeichen des Texts, die entfernt wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)