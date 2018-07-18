---
title: JsAddRef-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsAddRef
helpviewer_keywords:
- JsAddRef function
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e55ab6643dd949b8b41962161f76648dba926e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567630"
---
# <a name="jsaddref-function"></a>JsAddRef-Funktion
Fügt einen Verweis auf ein Objekt mit Garbage Collection hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ref`  
 Das Objekt, dem ein Verweis hinzugefügt werden soll.  
  
 `count`  
 Die neue Verweisanzahl des Objekts (kann NULL übergeben).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Dies muss nur für `JsRef`-Handles aufgerufen werden, die nicht irgendwo im Stapel gespeichert werden sollen. Mit dem Aufrufen von `JsAddRef` wird sichergestellt, dass das Objekt, auf das der `JsRef` verweist, erst freigegeben wird, wenn `JsRelease` aufgerufen wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)