---
title: 'Idebugpointerfield:: getdereferencedfield | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02197f660189d4caf374fc5927f349fd5fc6b8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201011"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt den Typ des Objekts zurück, auf das dieses Zeiger Objekt zeigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 vorgenommen Gibt ein [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Typ des Zielobjekts beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn das [idebugpointerfield](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt z. b. auf eine ganze Zahl zeigt, beschreibt der von dieser Methode zurückgegebene [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Typ diesen ganzzahligen Typ.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugpointerfield](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
