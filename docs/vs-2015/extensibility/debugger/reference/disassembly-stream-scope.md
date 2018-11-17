---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17ff0198b0472d63f070bc595b690f5cf252263a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810051"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Bereich des Datenstroms Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 DSS_HUGE  
 Gibt an, dass die Disassemblierung der Codekontext würde mehr Ausgabedaten als ein Client in der Regel in einem einzigen Aufruf abrufen möchten.  
  
 DSS_FUNCTION  
 Gibt an, dass die Funktion der Codekontext enthaltenen disassembliert werden soll. Gibt an, dass es sich bei den Disassembly-Stream eine Funktion darstellt, nach der Rückkehr von der [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) Methode.  
  
 DSS_MODULE  
 Bei Rückgabe durch die `IDebugDisassemblyStream2::GetScope` -Methode gibt an, dass der Disassembly Stream ein Moduls darstellt.  
  
 DSS_ALL  
 Gibt die Disassembly für den gesamten Adressraum an.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) Methode und zurückgegeben, indem die [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) Methode.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)

