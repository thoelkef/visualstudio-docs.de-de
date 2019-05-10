---
title: EncUnavailableReason | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957290"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Stellt die Gründe, **bearbeiten und Fortfahren** ist nicht verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
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
 Keine bestimmten Grund für bearbeiten und Fortfahren nicht verfügbar.  
  
 ENCUN_INTEROP  
 Bearbeiten und Fortfahren ist während eines Interop-Aufrufs nicht verfügbar.  
  
 ENCUN_SQLCLR  
 Bearbeiten und Fortfahren ist während eines Aufrufs der SQL-Prozedur, das die Common Language Runtime (CLR) wird verwendet, nicht verfügbar.  
  
 ENCUN_MINIDUMP  
 Bearbeiten und Fortfahren ist während der Verarbeitung eines Minidump nicht verfügbar.  
  
 ENCUN_EMBEDDED  
 Bearbeiten und Fortfahren ist nicht verfügbar, bei der Verarbeitung von eingebetteten Codes.  
  
 ENCUN_ATTACH  
 Bearbeiten und Fortfahren wird nicht verfügbar, da die Sitzung an angefügt wurde, nicht gestartet, durch den Debugger.  
  
 ENCUN_WIN64  
 Bearbeiten und Fortfahren ist während der Verarbeitung von 64-Bit-Windows-Code nicht verfügbar.  
  
## <a name="remarks"></a>Hinweise  
 Diese Enumeration ist für die interne Verwendung nur durch [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Die [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) und [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) Methoden wie von einem benutzerdefinierten Port Lieferanten implementiert, sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
