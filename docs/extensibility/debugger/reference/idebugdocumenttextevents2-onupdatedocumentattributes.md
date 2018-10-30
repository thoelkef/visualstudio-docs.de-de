---
title: IDebugDocumentTextEvents2::onUpdateDocumentAttributes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bda3f7869715b3c0ab08d64cdb7ef1f13ca4898
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816728"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
Benachrichtigt Empfänger des Ereignisses, dass die Attribute des Dokuments aktualisiert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```csharp  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `textdocattr`  
 [in] Eine Kombination von Flags aus der [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) Enumeration, die die aktualisierten Attribute des Dokuments angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)