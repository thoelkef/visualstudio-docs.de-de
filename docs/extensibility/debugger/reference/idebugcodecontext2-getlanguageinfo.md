---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9b624b05dd688ef74bba6e7ab44a09337bbb9b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991917"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ruft die Sprachinformationen für diesen Codekontext ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrLanguage`  
 [in, out] Gibt eine Zeichenfolge mit dem Namen der Sprache, z. B. "C++".  
  
 `pguidLanguage`  
 [in, out] Beispielsweise gibt die GUID für die Sprache der Codekontext `guidCPPLang`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Mindestens einer der Parameter muss einen Wert ungleich Null zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)