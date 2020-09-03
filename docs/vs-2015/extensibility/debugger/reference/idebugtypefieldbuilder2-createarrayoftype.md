---
title: 'IDebugTypeFieldBuilder2:: kreatearrayoftype | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b02b7c6ef29e1b6c00b5d5a0b7fbfa93c03f132b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152890"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt ein Array des angegebenen Typs und der angegebenen Größe.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeField`  
 in Typ der Elemente, die das Array enthalten soll.  
  
 `rank`  
 in Anzahl der Elemente im Array.  
  
 `pArrayOfTypeField`  
 vorgenommen Gibt die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekte zurück, die das neue Array darstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)
