---
title: 'Idebugmethodfield:: iscustomattributedefined | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fcc496131cd27837dc53fe2ecba05cf6b2c44d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162558"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCustomAttributeName`  
 in Eine Zeichenfolge mit dem Namen des zu suchenden benutzerdefinierten Attributs.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für diese Methode definiert ist; andernfalls wird S_FALSE zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
