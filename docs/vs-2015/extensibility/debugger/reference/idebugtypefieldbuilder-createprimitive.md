---
title: IDebugTypeFieldBuilder::CreatePrimitive | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54cf6ecbadfb5b710f16f76539be6a9a503d6647
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784389"
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt ein Objekt, das einen primitiven Typ darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreatePrimitive (  
   DWORD          dwElementType,  
   IDebugField ** pTypeField  
);  
```  
  
```csharp  
int CreatePrimitive (  
   uint            dwElementType,  
   out IDebugField pTypeField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwElementType`  
 [in] Wert aus der [CorElementType-Enumeration](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , den primitiven Typ darstellt.  
  
 `pTypeField`  
 [out] Gibt die IDebugField-Schnittstelle für den neuen Typ zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)

