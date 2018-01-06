---
title: IDebugDocumentTextEvents2::onRemoveText | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords: IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2cf12a1bac44755422719f7ab6d62f63380ee4f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 [in] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, der angibt, aus der Text entfernt wurde.  
  
 `dwNumToRemove`  
 [in] Gibt die Anzahl der Zeichen des Texts, die entfernt wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)