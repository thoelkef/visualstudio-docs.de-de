---
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97494f2180d0aede2dfd8e1a539a0d957f9a0bcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150077"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt den Wert eines Register fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 in Ein Wert aus der [CV_HREG_e Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) -Enumeration, die das Register angibt, in das geschrieben werden soll.  
  
 `NewVal`  
 in Der neue Registrierungs Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Trotz der Größe des Werts sollte in einer-Implementierung nur das, was das Register normalerweise enthält, gespeichert werden. Beispielsweise würde ein 8-Bit-Register nur die niedrigsten 8 Bits des angegebenen Werts enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)
