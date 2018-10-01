---
title: IDiaStackWalkHelper::readMemory | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8ef913a94dc184339d6c20c97ca8c3f0f3054a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515655"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaStackWalkHelper::readMemory](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-readmemory).  
  
Liest einen Block von Daten aus der ausführbaren Datei Image im Arbeitsspeicher.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 [in] Ein Wert aus der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumeration, die den Typ des Arbeitsspeichers zu lesen.  
  
 VA  
 [in] Virtuelle Adresse in das Image aus dem gelesen werden soll.  
  
 `cbData`  
 [in] Die Größe des Datenpuffers in Byte.  
  
 `pcbData`  
 [out] Gibt die Anzahl der tatsächlich gelesenen Bytes. Wenn `pbData` ist `NULL`, ist dies die Gesamtanzahl der Bytes der Daten zur Verfügung.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit dem Arbeitsspeicher lesen gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)



