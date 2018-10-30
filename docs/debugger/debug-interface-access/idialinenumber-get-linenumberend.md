---
title: 'Idialinenumber:: Get_linenumberend | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6a0dfff78c54c1e051e04c33ae73d82691bf0d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896392"
---
# <a name="idialinenumbergetlinenumberend"></a>IDiaLineNumber::get_lineNumberEnd
Ruft ab, die 1-basierte Zeilennummer, an dem die Anweisung oder den Ausdruck endet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_lineNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Zeilennummer, an dem endet die Anweisung oder den Ausdruck zurück. Wenn der Wert 0 (null) ist, ist die End-Informationen nicht vorhanden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)