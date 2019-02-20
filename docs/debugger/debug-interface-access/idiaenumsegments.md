---
title: IDiaEnumSegments | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39ac47f107c7365e2932d36084b2fc114934daba
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227354"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Listet die verschiedenen Segmente, die in der Datenquelle enthalten sind.

## <a name="syntax"></a>Syntax

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDiaEnumSegments`.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Ruft die [IEnumVARIANT-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) Version von diesem Enumerator.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Ruft die Anzahl der Segmente ab.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Ruft ein Segment mithilfe eines Indexes ab.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Überspringt eine angegebene Anzahl von Segmenten in einer Enumerationsfolge.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|

## <a name="remarks"></a>Anmerkungen

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie diese Schnittstelle durch Aufrufen der `QueryInterface` Methode für ein [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Objekt. Siehe das Beispiel für Details.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie Sie erhalten die `IDiaEnumSections` Schnittstelle aus einer Tabelle. Ein vollständigeres Beispiel der Verwendung von Segmenten, finden Sie unter den [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Schnittstelle.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
[Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
