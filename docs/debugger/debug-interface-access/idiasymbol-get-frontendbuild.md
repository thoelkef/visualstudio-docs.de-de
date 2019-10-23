---
title: 'Idiasymmetribol:: get_frontEndBuild | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a23db75b2e62e3ffbe2d17f14e36806c2dbb9955
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740664"
---
# <a name="idiasymbolget_frontendbuild"></a>IDiaSymbol::get_frontEndBuild
Ruft die Buildnummer des Front-Ends ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_frontEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Front-End-Buildnummer zurück. Siehe Hinweise.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Ein Compiler besteht in der Regel aus zwei primären Elementen: dem Front-End (dem Parser), das die Analyse des Quellcodes in ein zwischen Formular und ein Back-End (Code Generator) behandelt, das das zwischen Formular in eine Assembly konvertiert. Es ist nicht ungewöhnlich, dass das Front-End eine andere Version als das Back-End hat.

 Eine Front-End-oder Back-End-Versionsnummer besteht aus drei Teilen: \<major >. \<minor >. \<build >, wobei \<major > die Hauptversionsnummer ist, \<minor > die neben Versionsnummer und \<build > die Buildnummer ist. Beispiel: 13.10.3077.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 7.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)