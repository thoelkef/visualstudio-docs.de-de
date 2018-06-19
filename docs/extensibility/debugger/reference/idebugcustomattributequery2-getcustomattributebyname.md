---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109674"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ruft die benutzerdefinierten Attribute Bytes, die den Namen des benutzerdefinierten Attributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCustomAttributeName`  
 [in] Eine Zeichenfolge, die mit dem Namen des benutzerdefinierten Attributs, der gesucht wird.  
  
 `ppBlob`  
 [in, out] Ein Array, das mit dem benutzerdefinierten Attribut Bytes ausgefüllt ist.  
  
 `pdwLen`  
 [in, out] Gibt die maximale Anzahl von Bytes im zurückzugebenden der `ppBlob` array und gibt die Anzahl der tatsächlich in das Array geschriebenen Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn das benutzerdefinierte Attribut nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie die `ppBlob` Parameter auf einen null-Wert die Anzahl der zurückzugebenden Attribute verfügbaren Bytes. Anschließend weisen Sie ein Array, und übergeben Sie dieses Arrays in für die `ppBlob` Parameter.  
  
 Die Attributdaten darstellen, die unformatierten Daten des benutzerdefinierten Attributs.  
  
 Wenn die `ppBlob` und `pdwLen` Parameter auf einen null-Wert festgelegt werden, diese Methode kann verwendet werden, um festzustellen, ob das benutzerdefinierte Attribut lediglich vorhanden ist. Eine einfachere Alternative ist jedoch zum Aufrufen der [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)