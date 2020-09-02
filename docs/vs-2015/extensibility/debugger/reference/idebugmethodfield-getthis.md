---
title: 'Idebugmethodfield:: GetThis | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 786f3986875518470ed5756a0f7b57f4f93f5ca2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563610"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den `this` ( `Me` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] )-Zeiger des-Objekts ab, das die-Methode enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClass`  
 vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das den "This"-Zeiger darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 In objektorientierten Sprachen gibt es in der Regel einen impliziten Zeiger auf die aktuelle Instanziierung einer Klasse. Dies wird `this` in c#/C + + und as in als `Me` bezeichnet [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
