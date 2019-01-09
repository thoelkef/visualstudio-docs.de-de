---
title: IDebugPropertyEnumType_All::GetName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fd535d983d477a86b83953cf56852789747bd0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091441"
---
# <a name="idebugpropertyenumtypeallgetname"></a>IDebugPropertyEnumType_All::GetName
Gibt einen BSTR, das mit dem Namen des der `EnumType`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pname`  
 [out] Einem BSTR mit dem Namen des der `EnumType`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPropertyEnumType_All-Schnittstelle](../../winscript/reference/idebugpropertyenumtype-all-interface.md)