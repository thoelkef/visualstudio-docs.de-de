---
title: 'Idebugclassfield:: enumkonstruktors | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd93f4867221f0b42f91fe1f96b8a8b464bf5aa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191038"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die Konstruktoren für diese Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cMatch`  
 in Ein Wert aus der [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) Enumeration, der den Typ der aufzuzählungs Konstruktoren angibt.  
  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Konstruktoren darstellt. Gibt einen NULL-Wert zurück, wenn keine Konstruktoren vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine Konstruktoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Element der-Enumeration ist ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt, das eine Konstruktormethode beschreibt.  
  
 Die Liste der Konstruktoren schließt in der Regel nicht die Standardkonstruktoren ein, die von einem Compiler bereitgestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
