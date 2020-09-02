---
title: 'Idebugcustomattribute:: GetName | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569269"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen des benutzerdefinierten Attributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bstrName`  
 vorgenommen Gibt eine Zeichenfolge zurück, die den Namen des benutzerdefinierten Attributs enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von dieser Methode zurückgegebene benannte entspricht dem Namen der Klasse, die verwendet wird, um das Attribut zu deklarieren. Dies entspricht möglicherweise nicht exakt dem Namen der benutzerdefinierten Attribut Klasse, da c# es zulässt, dass das Suffix "Attribute" aus einem benutzerdefinierten Attributnamen gelöscht wird, wenn es in einer Deklaration verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
