---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe37c7157f96a905e52fb6656d5ebb8ff6f4971a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105618"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Ruft die Größe des Texts an dieser Position im Dokument ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcNumLines`  
 [out] Gibt die Anzahl der Textzeilen zurück.  
  
 `pcNumChars`  
 [out] Gibt die Anzahl der Zeichen des Texts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 [Nur C++] Wenn Sie ein bestimmter Wert nicht erwünscht ist, übergeben Sie NULL für den Parameter an.  
  
 [C#] Beide Parameter müssen angegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)