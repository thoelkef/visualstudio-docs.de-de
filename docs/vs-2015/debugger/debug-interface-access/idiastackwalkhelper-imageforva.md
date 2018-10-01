---
title: 'Idiastackwalkhelper:: Imageforva | Microsoft-Dokumentation'
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
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a67d092f811f621fe0cffa890c2455f3385f98c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512226"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiastackwalkhelper:: Imageforva](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-imageforva).  
  
Gibt den Anfang einer ausführbaren Datei des Image im Arbeitsspeicher eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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



