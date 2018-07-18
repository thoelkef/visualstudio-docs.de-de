---
title: EncUnavailableReason | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf705015925145b790b14a44007fed8d8fad3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101770"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Stellt die Gründe, **bearbeiten und Fortfahren** ist nicht verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 ENCUN_NONE  
 Keinen bestimmten Grund, warum bearbeiten und Fortfahren steht nicht zur Verfügung.  
  
 ENCUN_INTEROP  
 Bearbeiten und Fortfahren ist während einer Interop-Aufrufen nicht verfügbar.  
  
 ENCUN_SQLCLR  
 Bearbeiten und Fortfahren steht nicht während eines SQL-Prozeduraufrufs, das die Common Language Runtime (CLR) verwendet.  
  
 ENCUN_MINIDUMP  
 Bearbeiten und Fortfahren ist bei der Verarbeitung eines Minidump nicht verfügbar.  
  
 ENCUN_EMBEDDED  
 Bearbeiten und Fortfahren ist nicht verfügbar, bei der Verarbeitung von eingebetteten Codes.  
  
 ENCUN_ATTACH  
 Bearbeiten und Fortfahren ist nicht verfügbar, da die Sitzung an angefügt wurde, nicht gestartet durch den Debugger.  
  
 ENCUN_WIN64  
 Bearbeiten und Fortfahren ist bei der Verarbeitung von Windows-64-Bit-Code nicht verfügbar.  
  
## <a name="remarks"></a>Hinweise  
 Diese Enumeration ist für die interne Verwendung nur durch [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. Die [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) und [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) Methoden, wie ein benutzerdefinierter Port Lieferant implementiert sollte stets `E_NOTIMPL`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)