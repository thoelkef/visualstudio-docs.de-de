---
title: IDiaEnumTables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45156a7a7c69c59a3b9ad53ca4d8f9afc4bf814a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200420"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Listet die verschiedenen Tabellen in der Datenquelle an.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaEnumTables`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Ruft die [IEnumVARIANT-Schnittstelle](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) Version von diesem Enumerator.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Ruft die Anzahl der Tabellen ab.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Ruft eine Tabelle über einen Index oder einen Namen ab.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Ruft eine angegebene Anzahl von Tabellen in der Enumerationsfolge ab.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Überspringt eine angegebene Anzahl von Tabellen in einer Enumerationsfolge.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) Methode.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie erhalten die `IDiaEnumTables` Schnittstelle aus einer Sitzung. Ein vollständigeres Beispiel der Verwendung von Tabellen finden Sie unter den [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Schnittstelle.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)



