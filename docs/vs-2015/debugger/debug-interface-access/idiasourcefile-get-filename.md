---
title: 'Idiasourcefile:: Get_filename | Microsoft-Dokumentation'
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
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7816f87d344467804e51060416950ba5eec2e20
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792046"
---
# <a name="idiasourcefilegetfilename"></a>IDiaSourceFile::get_fileName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Namen der Quelldatei ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_fileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Namen der Quelldatei zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)



