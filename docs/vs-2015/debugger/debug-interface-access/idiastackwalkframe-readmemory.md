---
title: 'Idiastackwalkframe:: ReadMemory | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2fd2fe46b9be7a3181945c9fd3e58e0b087472d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942126"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest Arbeitsspeicher aus Image an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 [in] Eines der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumerationswerte, der angibt, die Art des Arbeitsspeichers auf.  
  
 `va`  
 [in] Speicherort der virtuellen Adresse in Abbildung gelesen werden soll.  
  
 `cbData`  
 [in] Größe des Datenpuffers in Byte.  
  
 `pcbData`  
 [out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes der Daten zur Verfügung.  
  
 `data`  
 [out] Ein Puffer, der mit Daten aus der angegebenen Position gefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



