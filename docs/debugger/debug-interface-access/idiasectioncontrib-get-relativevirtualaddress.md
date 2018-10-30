---
title: 'Idiasectioncontrib:: Get_relativevirtualaddress | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relativeVirtualAddress method
ms.assetid: 32f9674d-94f1-4590-99de-a2eb60da4af8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25fce77625d00cdcf3c76691e60a7bf2feafe6b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825789"
---
# <a name="idiasectioncontribgetrelativevirtualaddress"></a>IDiaSectionContrib::get_relativeVirtualAddress
Ruft das Bild relative virtuelle Adresse (RVA) des Beitrags ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt das Bild-RVA des Beitrags zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)