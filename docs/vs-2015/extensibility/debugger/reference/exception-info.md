---
title: EXCEPTION_INFO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 152ddae9ad5c3c6b6119c146d428024bc2e26a95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513625"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [EXCEPTION_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/exception-info).  
  
Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgegeben, die von der zu debuggende Programm wird ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Member  
 pProgram  
 Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in dem die Ausnahme aufgetreten ist.  
  
 bstrProgramName  
 Der Name des Programms in der die Ausnahme aufgetreten ist.  
  
 bstrExceptionName  
 Der Name der Ausnahme.  
  
 dwCode  
 Die ID-Code für die Ausnahme oder ein Laufzeit-Fehler.  
  
 dwState-Datenmember  
 Ein Wert aus der [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Enumeration, die den Zustand der Ausnahme definiert.  
  
 guidType  
 Die GUID für die Sprache, entweder `guidLang` oder `guidEng`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Parameter an übergeben die [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) und [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Methoden. Diese Struktur wird ebenfalls übergeben, um die [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) Methode gefüllt werden soll.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)

