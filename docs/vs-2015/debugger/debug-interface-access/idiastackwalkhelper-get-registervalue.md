---
title: 'IDiaStackWalkHelper:: get_registerValue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4dde30ebcda46d75271b15ec5b7f7c1ac49f384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150114"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Wert eines Register ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 in Ein Wert aus der [CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumerationsenumeration, die angibt, von welchem Register der Wert abgeleitet werden soll.  
  
 `pRetVal`  
 vorgenommen Gibt den aktuellen Wert des Register zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Trotz der Größe des- `pRetVal` Parameters sollte eine-Implementierung nur das, was das Register normalerweise enthält, speichern. Ein 8-Bit-Register enthält z. b. nur die niedrigsten 8 Bits des angegebenen-Werts. Dieser 8-Bit-Wert wird auf 64 Bit erweitert, wenn er von dieser Methode zurückgegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)
