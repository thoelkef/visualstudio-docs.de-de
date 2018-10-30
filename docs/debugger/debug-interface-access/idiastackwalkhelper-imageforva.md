---
title: 'Idiastackwalkhelper:: Imageforva | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4942a88378091d890507c1121f6863c309c40662
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823034"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Gibt den Anfang einer ausführbaren Datei des Image im Arbeitsspeicher eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei zurück.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `vaContext`  
 [in] Die virtuelle Adresse, die sich an einer beliebigen Stelle in der ausführbaren Datei Leerzeichen.  
  
 `pvaImageStart`  
 [out] Gibt zurück, die virtuelle Startadresse des Images von der ausführbaren Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)