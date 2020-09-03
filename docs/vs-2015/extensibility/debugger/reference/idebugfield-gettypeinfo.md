---
title: 'Idebugfield:: gettypeingefo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4229bef0460c7475cda3f81d06b6b24e38ed759
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148908"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft typunabhängige Informationen über das Symbol oder den Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeInfo`  
 vorgenommen Gibt Typinformationen in der angegebenen [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Typunabhängige Informationen sind z. b. die AppDomain, das Modul und die Klasse, die das Symbol enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
