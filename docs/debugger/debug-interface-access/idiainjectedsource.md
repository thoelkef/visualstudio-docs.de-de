---
title: Idiainjetedsource | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 994f454372883f2516d1eab03bf1152693969b16
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743305"
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
Greift auf injizierten, in der Dia-Datenquelle gespeicherten Quellcode zu.

## <a name="syntax"></a>Syntax

```
IDiaInjectedSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaInjectedSource` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Ruft eine zyklische Redundanz Überprüfung (CRC) ab, die aus den Bytes des Quellcodes berechnet wird.|
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Ruft die Anzahl der Code Bytes ab.|
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Ruft den Dateinamen für die Quelle ab.|
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Ruft den Namen der Objektdatei ab, in die die Quelle kompiliert wurde.|
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Ruft den Namen des angegebenen nicht-Datei Quellcodes ab. Das heißt, Code, der eingefügt wurde.|
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Ruft den Indikator der verwendeten Quell Komprimierung ab.|
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Ruft die Quell Code Bytes ab.|

## <a name="remarks"></a>Hinweise
Eingefügte Quelle ist Text, der während der Kompilierung eingefügt wird. Dies bedeutet nicht, dass die Präprozessor`#include` C++in verwendet werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der [idiaenuminjetedsources:: Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) -Methode oder der [idiaenuminjetedsources:: Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) -Methode ab. Ein Beispiel für das Abrufen der `IDiaInjectedSource`-Schnittstelle finden Sie unter [idiaenuminjetedsources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) -Schnittstelle.

## <a name="example"></a>Beispiel
In diesem Beispiel werden die Daten in der `IDiaInjectedSource`-Schnittstelle angezeigt. Eine alternative Vorgehensweise bei Verwendung der [idiapropertystorage](../../debugger/debug-interface-access/idiapropertystorage.md) -Schnittstelle finden Sie im Beispiel in der [idiaenuminjetedsources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) -Schnittstelle.

```C++
void PrintInjectedSource(IDiaInjectedSource* pSource)
{
    ULONGLONG codeLength      = 0;
    DWORD     crc             = 0;
    DWORD     compressionType = 0;
    BSTR      sourceFilename  = NULL;
    BSTR      objectFilename  = NULL;
    BSTR      virtualFilename = NULL;

    std::cout << "Injected Source:" << std::endl;
    if (pSource != NULL)
    {
        if (pSource->get_crc(&crc) == S_OK &&
            pSource->get_sourceCompression(&compressionType) == S_OK &&
            pSource->get_length(&codeLength) == S_OK)
        {
            wprintf(L"  crc = %lu\n", crc);
            wprintf(L"  code length = %I64u\n",codeLength);
            wprintf(L"  compression type code = %lu\n", compressionType);
        }

        wprintf(L"  source filename: ");
        if (pSource->get_filename(&sourceFilename) == S_OK)
        {
            wprintf(L"%s", sourceFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  object filename: ");
        if (pSource->get_filename(&objectFilename) == S_OK)
        {
            wprintf(L"%s", objectFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        wprintf(L"  virtual filename: ");
        if (pSource->get_filename(&virtualFilename) == S_OK)
        {
            wprintf(L"%s", virtualFilename);
        }
        else
        {
            wprintf(L"<none>");
        }
        wprintf(L"\n");

        SysFreeString(sourceFilename);
        SysFreeString(objectFilename);
        SysFreeString(virtualFilename);
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)
- [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
