---
title: IDebugDisassemblyStream2::GetDocument | Microsoft-Dokumentation
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
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c260209c59ab425e3474aa9c82882da8d1c6d92e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523489"
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDisassemblyStream2::GetDocument](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-getdocument).  
  
Ruft das Quelldokument, das diesen Eingabedatenstrom zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrDocumentUrl`  
 [in] Die URL des Dokuments.  
  
 `ppDocument`  
 [out] Gibt eine [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Objekt, das das Dokument darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von Debug-Engines implementiert, die Text-Dokumenten, die nicht in eine tatsächliche Datei gespeichert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

