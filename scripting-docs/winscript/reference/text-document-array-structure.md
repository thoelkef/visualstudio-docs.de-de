---
title: TEXT_DOCUMENT_ARRAY-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d188729b68f8086da62d40ca28fc29945c8be7f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152235"
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY-Struktur
Ein Array von [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md) Objekte. Elemente werden mit CoTaskMemAlloc zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Member  
 `dwCount`  
 Die Anzahl der Dokumente.  
  
 `Members`  
 Der Satz von Dokumenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)