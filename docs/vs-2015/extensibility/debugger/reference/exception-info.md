---
title: EXCEPTION_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66af4d95707be99865df3df32751215cf5eb10b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181173"
---
# <a name="exception_info"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt eine Ausnahme oder einen Laufzeitfehler, der von dem Programm ausgelöst wird, das deentschlgt wird.  
  
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
 Pprogram  
 Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, in dem die Ausnahme aufgetreten ist.  
  
 bstrauprogramname  
 Der Name des Programms, in dem die Ausnahme aufgetreten ist.  
  
 bstrexceptionname  
 Der Name der Ausnahme.  
  
 dwcode  
 Der Identifikationscode für die Ausnahme oder den Laufzeitfehler.  
  
 dwstate  
 Ein Wert aus der [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Enumeration, die den Zustand der Ausnahme definiert.  
  
 guidtype  
 Der GUID-Sprachen Bezeichner, entweder `guidLang` oder `guidEng` .  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird als Parameter an die Methoden " [abtexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) " und " [removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) " übergeben. Diese Struktur wird auch an die [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) -Methode übergeben, die ausgefüllt werden soll.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 ["Abtexception"](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [Removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
