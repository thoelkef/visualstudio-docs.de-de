---
title: BSTR_ARRAY | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912537eb632768b3bcb6543dab098126ce02424f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153181"
---
# <a name="bstr_array"></a>BSTR_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Eine-Struktur, die ein Array von Zeichen folgen beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 dwCount  
 Anzahl der Zeichen folgen im `Members` Array.  
  
 Member  
 Array von Zeichen folgen.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird von der [enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) -Methode zurückgegeben.  
  
 [Nur C++] Jede einzelne Zeichenfolge muss mit freigegeben werden `SysFreeString` , und das `Members` Array muss mit freigegeben werden `CoTaskMemFree` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
