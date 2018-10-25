---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c2638a072c3cf7c234adc88c26bace3348533f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931024"
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