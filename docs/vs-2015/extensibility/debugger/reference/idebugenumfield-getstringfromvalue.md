---
title: 'Idebugenenfield:: getstringfromvalue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188996"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode erhält den Namen der Enumerationskonstante, wenn ihr Wert angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 in Der Wert, für den der Name der Enumerationskonstante angezeigt werden soll.  
  
 `pbstrValue`  
 vorgenommen Gibt den Namen der Enumerationskonstante zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` Wenn der Wert keinen zugeordneten Namen hat, oder es wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn dem gleichen Wert mehr als ein Name zugeordnet ist, wird der Vorname zurückgegeben, der in der-Enumeration definiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
