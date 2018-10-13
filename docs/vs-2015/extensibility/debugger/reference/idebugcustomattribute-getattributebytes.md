---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20f57efad2e7af5325c335646bf5a9cf0d7c3b1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297083"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Attributinformationen, wie ein Blob von Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in, out] Ein Array, das mit dem Attribut Bytes gefüllt ist.  
  
 `pdwLen`  
 [in, out] Gibt die maximale Anzahl der Bytes, die in Zurückgeben der `ppBlob` array und gibt die Anzahl der tatsächlich in das Array geschriebenen Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie die `ppBlob` Parameter, um einen null-Wert die Anzahl der zurückzugebenden Attribute verfügbaren Bytes. Anschließend ordnen Sie ein Array, und übergeben Sie dieses Array in für die `ppBlob` Parameter.  
  
 Die Attribut-Bytes stellen die unformatierten Daten des benutzerdefinierten Attributs dar.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

