---
title: JS_PROPERTY_ATTRIBUTES-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a3fac8b1be15d1b1d26c13fe1e17e311798a3a3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088269"
---
# <a name="jspropertyattributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES-Enumeration
Zeigt die Attribute einer Eigenschaft an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Member  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Die Eigenschaft weist keine Attribute auf.|  
|`JS_PROPERTY_HAS_CHILDREN`|Die Eigenschaft weist untergeordnete Elemente auf.|  
|`JS_PROPERTY_FAKE`|Die Eigenschaft stellt einen falschen Knoten, z. B. "[Methoden]".|  
|`JS_PROPERTY_METHOD`|Die Eigenschaft ist eine Methode.|  
|`JS_PROPERTY_READONLY`|Die Eigenschaft ist schreibgeschützt.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Die Eigenschaft ist ein Zeiger auf ein systemeigenes WinRT-Objekt.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)