---
title: 'Idebugproperty:: GetParent | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ca05935ea3565cb8e6237c36ed60b412bdcd418
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562350"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Ruft die übergeordnete Eigenschaft einer Eigenschaft ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppParent`  
 vorgenommen Gibt die `IDebugProperty`-Schnittstelle zurück, die das übergeordnete Element der Eigenschaft darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)