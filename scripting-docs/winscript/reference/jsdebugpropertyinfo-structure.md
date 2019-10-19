---
title: Jsdebugpropertyinfo-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6c6470386414158a53794d1a5c580492edc0e15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572298"
---
# <a name="jsdebugpropertyinfo-structure"></a>JsDebugPropertyInfo-Struktur
Gibt Informationen über eine Eigenschaft an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Member  
 `name`  
 Den Namen der Eigenschaft.  
  
 `type`  
 Den Typ der Eigenschaft.  
  
 `value`  
 Der Wert der Eigenschaft.  
  
 `fullName`  
 Der vollständige Name der Eigenschaft.  
  
 `attr`  
 Eine Enumeration, die die Eigenschaftsattribute darstellt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)