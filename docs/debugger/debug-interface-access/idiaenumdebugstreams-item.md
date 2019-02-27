---
title: 'Idiaenumdebugstreams:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f07ecb151b6bf2cd4a9d48fbe6596bc7a533f97a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598673"
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Ruft eine Debugstream über einen Index oder Name ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item (
    VARIANT                   index,
    IDiaEnumDebugStreamData** stream
);
```

#### <a name="parameters"></a>Parameter
Index

[in] Index oder Name der Debug-Stream abgerufen werden sollen. Wenn eine ganze Zahl Variante verwendet wird, muss es im Bereich von 0 bis `count`-1 und, in denen `count` ist von zurückgegeben der [idiaenumdebugstreams:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) Methode.

Stream

[out] Gibt eine [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) Objekt, das den angegebenen Debug-Stream darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel

```C++
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,
                                       LONG whichStream)
{
    IDiaEnumDebugStreamData *pStreamData = NULL;
    if (pStreamList != NULL)
    {
        LONG numStreams = 0;
        if (pStreamList->get_count(&numStreams) == S_OK &&
            whichStream >= 0 && whichStream < numStreams)
        {
            VARIANT vIndex;
            vIndex.vt   = VT_I4;
            vIndex.lVal = whichStream;
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)
            {
                std::cerr << "Error retrieving stream " << whichStream << std::endl;
            }
        }
    }
    return(pStreamData);
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
