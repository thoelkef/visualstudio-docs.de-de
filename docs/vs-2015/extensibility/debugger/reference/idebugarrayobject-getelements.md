---
title: 'Idebugarrayobject:: getElements | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cad81d76e2fcec01fa50a37fa6ab6cb49cfc79be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423698"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft einen Enumerator für alle Elemente des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebugobjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) -Objekt zurück, das das Auflisten aller Elemente ermöglicht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie als Alternative die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) -Methode und die [getelate](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) -Methode, um die Elemente zu durchlaufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
