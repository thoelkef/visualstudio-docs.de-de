---
title: Idebugpointerobject::D ereferenzierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40a0e66e5f3cb3a50618a3c8dd4fd5926c34c624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201005"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Objekt ab, auf das verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwIndex`  
 in Ein einfacher Byte Offset vom Anfang des Objekts, auf das verwiesen wird.  
  
 `ppObject`  
 vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das Objekt darstellt, auf das verwiesen wird, plus Offset, falls vorhanden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht auf ein anderes Objekt verweist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Objekt, auf das gezeigt wird, kann ein primitiver oder komplexer Typ sein, z. b. eine Klasse oder Struktur.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
