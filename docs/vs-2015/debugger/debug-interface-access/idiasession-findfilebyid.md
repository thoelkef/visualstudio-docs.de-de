---
title: 'Idiasession:: Findfilebyid | Microsoft-Dokumentation'
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
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f324f76f711f0bd2e03a11c595bb696a137f8b61
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304972"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Quelldatei von Datei-ID ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uniqueId`  
 [in] Gibt den Bezeichner der Datei an.  
  
 `ppResult`  
 [out] Gibt eine [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) abgerufene Objekt, das die Quelldatei darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Bezeichner der Datei ist ein eindeutiger Wert, der intern verwendet, um die DIA-SDK damit alle Quelldateien eindeutig ist. Diese Methode wird in der Regel intern die DIA-SDK verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession:: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)



