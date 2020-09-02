---
title: 'Idiapropertystorage:: Read PropertyNames | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537354"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft entsprechende Zeichen folgen Namen für angegebene Eigenschaften Bezeichner ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpropid`  
 in Anzahl der Eigenschaften-IDs in `rgpropid` .  
  
 `rgpropid`  
 in Ein Array von Eigenschaften-IDs, für die die Namen abzurufen `PROPID` sind (wird in Wtypes. h als definiert `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Array von Eigenschaften Namen für die angegebenen Eigenschaften-IDs. Das Array muss vorab zugeordnet werden, um die angeforderte Anzahl von Eigenschaftsnamen zu speichern, und es muss mindestens Zeichen folgen enthalten können `cpropid``BSTR` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die zurückgegebenen Eigenschaftsnamen müssen freigegeben werden (durch Aufrufen der- `SysFreeString` Funktion), wenn Sie nicht mehr benötigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
