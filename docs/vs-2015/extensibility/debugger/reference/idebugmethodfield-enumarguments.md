---
title: 'Idebugmethodfield:: enumarguments | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5744e25f76676e70e25777596fb0d8eb3a580511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205235"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für den Typ jedes Arguments, das erforderlich ist, um die Methode aufzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppParams`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Argument Typen darstellt. Gibt einen NULL-Wert zurück, wenn keine Argumente vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben oder S_FALSE zurückgegeben, wenn keine Argumente vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Element ist ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das die Typen der einzelnen Parameter darstellt. Rufen Sie die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) -Methode auf, um Informationen über den Typ der einzelnen Parameter abzurufen.  
  
 Wenn der Name des Parameters zusammen mit dem Typ benötigt wird, müssen Sie die [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) -Methode aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
