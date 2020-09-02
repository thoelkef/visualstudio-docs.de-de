---
title: 'Idebugcustomattribute:: gettientfield | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b6d6ceadc8ee0dc6099d6463a75f1c792837e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569575"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Feld ab, an das das benutzerdefinierte Attribut angefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 vorgenommen Gibt das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt zurück, das das Feld darstellt, an das das benutzerdefinierte Attribut angefügt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Aufrufen der [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für das zurückgegebene [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, um zu bestimmen, welche Art von Feld das übergeordnete Element ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
