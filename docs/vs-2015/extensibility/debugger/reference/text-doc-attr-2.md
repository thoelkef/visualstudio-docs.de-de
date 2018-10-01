---
title: TEXT_DOC_ATTR_2 | Microsoft-Dokumentation
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
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80263e50de833942c42f7762e435c75e3dfc821e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515352"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [TEXT_DOC_ATTR_2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/text-doc-attr-2).  
  
Beschreibt die Attribute eines Dokuments.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```csharp  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## <a name="members"></a>Member  
 TEXT_DOC_ATTR_READONLY_2  
 Gibt an, dass das Dokument schreibgeschützt ist.  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Dieser Wert ist nicht tatsächlich in der Assembly für C#-Code definiert. Stattdessen müssen Sie die Definition Ihrer Quelldatei kopieren.  
  
 Übergeben als Argument an die [OnUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)

