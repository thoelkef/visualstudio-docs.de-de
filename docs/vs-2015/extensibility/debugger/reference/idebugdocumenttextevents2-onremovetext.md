---
title: 'IDebugDocumentTextEvents2:: onremovetext | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ff2f3685250d9a4f6cbad9c1341a5e17b0641b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149329"
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Benachrichtigt das Debugpaket, dass der Text aus dem Dokument entfernt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die angibt, wo der Text entfernt wurde.  
  
 `dwNumToRemove`  
 in Gibt die Anzahl der zu entfernenden Textzeichen an.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
