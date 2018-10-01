---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35bce0368c9f14fa135caedd27bdf3aa9d0ae208
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513938"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDocumentTextEvents2::onUpdateTextAttributes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes).  
  
Benachrichtigt dem debugpaket, Text-Attribute im Dokument aktualisiert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT onUpdateTextAttributes(   
   TEXT_POSITION pos,  
   DWORD         dwNumToUpdate  
);  
```  
  
```csharp  
int onUpdateTextAttributes(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pos`  
 [in] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die angibt, in denen die Textattribute aktualisiert wurden.  
  
 `dwNumToUpdate`  
 [in] Gibt die Anzahl der Zeichen des Texts, die aktualisiert wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

