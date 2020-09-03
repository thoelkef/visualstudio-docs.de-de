---
title: 'Idiainjetedsource:: get_virtualFilename | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09612077baf6bbf6eb4ed84334c0d7cbc4d88519
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203631"
---
# <a name="idiainjectedsourceget_virtualfilename"></a>IDiaInjectedSource::get_virtualFilename
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Namen des angegebenen nicht-Datei Quellcodes ab. Das heißt, Code, der eingefügt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualFilename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Namen des eingefügten nicht-Datei-Quellcodes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
