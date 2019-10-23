---
title: Idiaenumerbugstreamdata | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5929f6f36c183d3a580ab605d313695cb584664
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744839"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
Ermöglicht den Zugriff auf die Datensätze in einem Debug-Datenstrom.

## <a name="syntax"></a>Syntax

```
IDiaEnumDebugStreamData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaEnumDebugStreamData` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Ruft die Version der [IEnumVARIANT-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dieses Enumerators ab.|
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Ruft die Anzahl der Datensätze im Debug-Datenstrom ab.|
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Ruft den Namen des debugdatenstreams ab.|
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Ruft den angegebenen Datensatz ab.|
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Ruft die angegebene Anzahl von Datensätzen aus der enumerationssequenz ab.|
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Überspringt eine angegebene Anzahl von Datensätzen in einer enumerationssequenz.|
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Erstellt einen Enumerator, der die gleiche aufgelistete Sequenz wie der aktuelle Enumerator enthält.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle stellt einen Datenstrom von Datensätzen in einem debugdatenstrom dar. Die Größe und die Interpretation der einzelnen Datensätze hängen von dem Datenstrom ab, aus dem der Datensatz stammt. Diese Schnittstelle ermöglicht den Zugriff auf die Rohdaten Bytes in der Symbol Datei.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie die [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) -Methode oder die [IDiaEnumDebugStreams:: Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) -Methode auf, um ein `IDiaEnumDebugStreamData` Objekt zu erhalten.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt, wie Sie auf einen einzelnen Datenstrom und seine Datensätze zugreifen können.

```C++
void PrintStreamData(IDiaEnumDebugStreamData* pStream)
{
    BSTR  wszName;
    LONG  dwElem;
    ULONG celt    = 0;
    DWORD cbData;
    DWORD cbTotal = 0;
    BYTE  data[1024];

    if(pStream->get_name(&wszName) != S_OK)
    {
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");
    }
    else
    {
        wprintf_s(L"Stream: %s", wszName);
        SysFreeString(wszName);
    }
    if(pStream->get_Count(&dwElem) != S_OK)
    {
        wprintf(L"ERROR - PrintStreamData() get_Count\n");
    }
    else
    {
        wprintf(L"(%d)\n", dwElem);
    }
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)
    {
        DWORD i;
        for (i = 0; i < cbData; i++)
        {
            wprintf(L"%02X ", data[i]);
            if(i && i % 8 == 7 && i+1 < cbData)
            {
                wprintf(L"- ");
            }
        }
        wprintf(L"| ");
        for(i = 0; i < cbData; i++)
        {
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');
        }
        wprintf(L"\n");
        cbTotal += cbData;
    }
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",
            cbTotal/dwElem, dwElem);
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
