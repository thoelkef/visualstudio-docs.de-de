---
title: TEXT_POSITION | Microsoft-Dokumentation
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
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60c29e078a42207b8862a4e06dc09b92f86d4989
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188876"
---
# <a name="textposition"></a>TEXT_POSITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt den Zeilen- und Spaltennummer Speicherort im angegebenen Text.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagTEXT_POSITION {   
   DWORD dwLine;  
   DWORD dwColumn;  
} TEXT_POSITION;  
```  
  
```csharp  
public struct TEXT_POSITION {   
   public uint dwLine;  
   public uint dwColumn;  
};  
```  
  
## <a name="members"></a>Member  
 dwLine  
 Index der Zeile in der Quelldatei.  
  
 dwColumn  
 Zeichen Offset in Zeile.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird verwendet, der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) und [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen.  
  
 Diese Struktur wird durch einen Aufruf für die folgenden Methoden ausgefüllt:  
  
-   [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
-   [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
  
-   [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)  
  
-   [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)  
  
 Diese Struktur wird als Parameter an die folgenden Methoden übergeben:  
  
-   [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)  
  
-   [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)  
  
-   [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)  
  
-   [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)  
  
-   [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)   
 [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)   
 [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

