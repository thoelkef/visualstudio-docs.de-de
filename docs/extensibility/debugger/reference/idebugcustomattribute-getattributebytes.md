---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords: IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1258b2b7fdc1c91eaaa6265ce74a3891deda8ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Ruft die Attributinformationen, wie ein Blob von Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppBlob`  
 [in, out] Ein Array, das mit der Attributdaten ausgefüllt ist.  
  
 `pdwLen`  
 [in, out] Gibt die maximale Anzahl von Bytes im zurückzugebenden der `ppBlob` array und gibt die Anzahl der tatsächlich in das Array geschriebenen Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie die `ppBlob` Parameter auf einen null-Wert die Anzahl der zurückzugebenden Attribute verfügbaren Bytes. Anschließend weisen Sie ein Array, und übergeben Sie dieses Arrays in für die `ppBlob` Parameter.  
  
 Die Attributdaten darstellen, die unformatierten Daten des benutzerdefinierten Attributs.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)