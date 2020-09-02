---
title: IDiaStackWalker::getEnumFrames2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25090ae66d28ebd9eb62f62f14979de1e82c5302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144719"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen Stapel Rahmen Enumerator für einen bestimmten Plattformtyp ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpuid`  
 in Ein Wert aus der [CV_CPU_TYPE_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) -Enumeration, die den Plattformtyp angibt.  
  
 `pHelper`  
 in Das [hilfsidiastackwalkhelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) -Objekt.  
  
 `ppEnum`  
 vorgenommen Gibt ein [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) -Objekt zurück, das eine Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) -Objekten enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie zum Abrufen einer Stapel Rahmen Liste nur für die x86-Plattform die [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) -Methode auf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
