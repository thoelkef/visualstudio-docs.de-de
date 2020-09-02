---
title: Idiapropertystorage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29832934b848729879ee1ba802c70f85117efd2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537627"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ermöglicht das Lesen der persistenten Eigenschaften eines Dia-Eigenschaften Satzes.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaPropertyStorage` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Ruft einen Zeiger auf einen Enumerator für Eigenschaften in diesem Satz ab.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Liest `BOOL` Werte in einem Eigenschaften Satz.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Liest `BSTR` Werte in einem Eigenschaften Satz.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Liest `DWORD` Werte in einem Eigenschaften Satz.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Liest `LONG` Werte in einem Eigenschaften Satz.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Liest Eigenschaftswerte in einem Eigenschaften Satz.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Ruft die entsprechenden Zeichen folgen Namen für angegebene Eigenschaften Bezeichner ab.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Liest `ULONGLONG` Werte in einem Eigenschaften Satz.|  
  
## <a name="remarks"></a>Bemerkungen  
 Jede Eigenschaft innerhalb eines Eigenschaften Satzes wird durch einen Eigenschafts Bezeichner (ID) identifiziert, d. h. ein vier Byte-Wert, der `ULONG` für diesen Satz eindeutig ist. Die Eigenschaften, die über die- `IDiaPropertyStorage` Schnittstelle verfügbar gemacht werden, entsprechen den Eigenschaften in der übergeordneten Schnittstelle. Beispielsweise kann auf die Eigenschaften der [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Schnittstelle über die-Schnittstelle über den Namen zugegriffen werden `IDiaPropertyStorage` (Beachten Sie jedoch, dass die-Eigenschaft für ein bestimmtes Objekt nicht gültig ist, obwohl die-Eigenschaft möglicherweise zugänglich ist `IDiaSymbol` ).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle ab, indem Sie die- `QueryInterface` Methode für eine andere Schnitt Die folgenden Schnittstellen können für die-Schnittstelle abgefragt werden `IDiaPropertyStorage` :  
  
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Funktion, die alle Eigenschaften anzeigt, die vom-Objekt verfügbar gemacht werden `IDiaPropertyStorage` . Ein Beispiel [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) dafür, wie die `IDiaPropertyStorage` Schnittstelle von der [idiainjetedsource](../../debugger/debug-interface-access/idiainjectedsource.md) -Schnittstelle abgerufen wird, finden Sie unter idiaenuminjetedsources-Schnittstelle.  
  
```cpp#  
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)  
{  
    IEnumSTATPROPSTG* pEnumProps;  
    STATPROPSTG       prop;  
    DWORD             celt = 1;  
  
    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)  
    {  
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)  
        {  
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };  
            PROPVARIANT vt = { VT_EMPTY };  
  
            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)  
            {  
                switch( vt.vt ){  
                    case VT_BOOL:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );  
                        break;  
                    case VT_I2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );  
                        break;  
                    case VT_UI2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );  
                        break;  
                    case VT_I4:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );  
                        break;  
                    case VT_UI4:  
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );  
                        break;  
                    case VT_UI8:  
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );  
                        break;  
                    case VT_BSTR:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );  
                        break;  
                    case VT_UNKNOWN:  
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );  
                        break;  
                    case VT_SAFEARRAY:  
                        break;  
                    default:  
                       break;  
                }  
                VariantClear((VARIANTARG*) &vt);  
            }  
        }  
        pEnumProps->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: getenumschlag Tables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
