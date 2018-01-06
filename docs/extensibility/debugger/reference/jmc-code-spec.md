---
title: JMC_CODE_SPEC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JMC_CODE_SPEC
helpviewer_keywords: JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18fb9177185dc7d863dcadd1a71bac0838a70a4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Diese Struktur wird verwendet, die JustMyCode-Informationen für ein Modul festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Member  
 fIsUserCode  
 Ungleich 0 (`TRUE`) Wenn das Modul ist, Benutzercode; berücksichtigt werden, andernfalls 0 (null) (`FALSE`) ist das Modul als externer Code behandelt werden und nicht gedebuggt werden.  
  
 bstrModuleName  
 Der Name des betreffenden Moduls.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als eine Liste von solchen Strukturen zu übergeben, die die [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)