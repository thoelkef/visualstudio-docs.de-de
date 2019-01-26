---
title: IDebugEnumField::GetValueFromString | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe0947158a93885278b2dbd4191d5ebb169aecee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987933"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Diese Methode gibt den Wert mit dem Namen einer Enumerationskonstante.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszValue`  
 [in] Eine Zeichenfolge, die den Namen für die zum Abrufen des Werts angeben. Beachten Sie, dass für C++, dies ist eine Breitzeichen-Zeichenfolge.  
  
 `pValue`  
 [out] Gibt den zugeordneten numerischen Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE`, wenn der Name nicht Teil der Enumeration oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist die Groß-/Kleinschreibung beachtet. Verwenden Sie bei Bedarf einen Groß-und Kleinschreibung gesucht (z. B. in einer Sprache wie Visual Basic-Namen, in denen keine Groß-/Kleinschreibung beachten sind) ist [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)