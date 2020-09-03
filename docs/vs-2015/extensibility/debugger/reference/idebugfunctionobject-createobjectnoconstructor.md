---
title: 'Idebugfunctionobject:: kreateobjectnoconstructor | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ea00035eb220ccd08590ceaea6db98944f4657a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179460"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt ein-Objekt ohne Konstruktor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pClassObject`  
 in Ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das den Typ des zu erstellenden Objekts darstellt.  
  
 `ppObject`  
 vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das neu erstellte-Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Struktur oder eines komplexen Typs darstellt (der keinen Konstruktor erfordert), bei dem es sich um einen Parameter für die Funktion handelt, die durch die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle dargestellt wird.  
  
 Wenn für den Object-Parameter ein Konstruktor erforderlich ist, müssen Sie die Methode "up [Object](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) " aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
