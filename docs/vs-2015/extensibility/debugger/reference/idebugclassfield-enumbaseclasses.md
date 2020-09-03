---
title: 'Idebugclassfield:: enumbaseclasses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acfdc872ba5f7cf1989ea1d9ec67f82f1c0419b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191043"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die Basisklassen dieser Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Basisklassen darstellt. Gibt einen NULL-Wert zurück, wenn keine Basisklassen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, S_SH_NO_BASE_CLASSES zurückgegeben, wenn keine Basisklassen vorhanden sind (und der- `ppEnum` Parameter auf einen NULL-Wert festgelegt ist); andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Basisklassen im Enumeratorobjekt werden in der Reihenfolge der unmittelbarsten (oder am meisten abgeleiteten) Basisklasse für die meisten Remote-Basisklassen angegeben. Beispielsweise mit den C++-Klassen:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 Die-Enumeration würde die Basisklassen in der Reihenfolge zurückgeben `Level2` , `Level1` , `Root` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
