---
title: "IDiaPropertyStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage-Schnittstelle"
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ermöglicht es Ihnen, die beibehaltenen Eigenschaften eines Durchmesser\-Eigenschaftensatzes zu lesen.  
  
## Syntax  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaPropertyStorage`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Ruft einen Zeiger auf einen Enumerator für Eigenschaften innerhalb dieses Satzes.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Liest `BOOL`\-Werte in einem Eigenschaft.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Liest `BSTR`\-Werte in einem Eigenschaft.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Liest `DWORD`\-Werte in einem Eigenschaft.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Liest `LONG`\-Werte in einem Eigenschaft.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Liest Eigenschaftswerte in einem Eigenschaft.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Ruft entsprechende Zeichenfolgennamens für den angegebenen Eigenschaftenbezeichner ab.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Liest `ULONGLONG`\-Werte in einem Eigenschaft.|  
  
## Hinweise  
 Jede Eigenschaft innerhalb des Eigenschaftensatzes wird durch einen Eigenschaftenbezeichner \(ID\), ein Wert BYTEs Vier `ULONG` identifiziert, der zum eindeutig ist, festlegen.  Die Eigenschaften, die von der `IDiaPropertyStorage`\-Schnittstelle verfügbar gemacht werden, entsprechen den Eigenschaften, die in der übergeordneten Schnittstelle zur Verfügung stehen.  Zum Beispiel können die Eigenschaften der [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Schnittstelle durch die `IDiaPropertyStorage`\-Schnittstelle über den Namen zugegriffen werden. \(Beachten Sie jedoch, dass, obwohl die Eigenschaft zugegriffen werden kann, möglicherweise nicht die Eigenschaft impliziert, ist für ein bestimmtes `IDiaSymbol`\-Objekt gültig.\)  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die `QueryInterface`\-Methode auf einer anderen Schnittstelle aufruft.  Die folgenden Schnittstellen können für die `IDiaPropertyStorage`\-Schnittstelle abgefragt werden:  
  
-   [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
-   [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
-   [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
-   [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
-   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
-   [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
-   [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## Beispiel  
 In diesem Beispiel wird eine Funktion veranschaulicht, die alle Eigenschaften anzeigt, die vom `IDiaPropertyStorage`\-Objekt verfügbar gemacht werden.  Zeigen Sie die [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)\-Schnittstelle als ein Beispiel dafür, wie die `IDiaPropertyStorage`\-Schnittstelle aus der [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)\-Schnittstelle ermittelt wird.  
  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)