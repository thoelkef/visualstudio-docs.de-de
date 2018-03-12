---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8d0e4535417f80198f06cb6b4255fea209b701e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszInterfaceName`  
 [in] Eine Zeichenfolge, die mit dem Schnittstellennamen, der gesucht wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, gibt "S_FALSE" zurück, wenn die Schnittstelle nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine Enumeration aller Schnittstellen wirksam und sucht die Liste für die entsprechende Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)