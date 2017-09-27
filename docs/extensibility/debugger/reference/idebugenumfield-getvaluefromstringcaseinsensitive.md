---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 68a5f199f389cb5bc24f0e648bb4719c1ad79545
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Diese Methode verwendet eine Suche Groß-/Kleinschreibung, um den zugeordneten Wert durch den Namen einer Enumerationskonstante zurückzugeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszValue`  
 [in] Eine Zeichenfolge, die den Namen für das Abrufen des Werts angeben. Beachten Sie, dass für C++, dies ist eine Zeichenfolge mit Breitzeichen.  
  
 `pValue`  
 [out] Gibt den zugeordneten numerischen Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE`, wenn der Name nicht Teil der Enumeration oder einen Fehlercode ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist die Groß-/Kleinschreibung. Wenn die Groß-/ Kleinschreibung (z. B. in einer anderen Sprache wie C++, in denen Groß-und Kleinschreibung) erforderlich ist, verwenden [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
