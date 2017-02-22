---
title: "IDiaEnumSegments | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments-Schnittstelle"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die verschiedenen Segmenten auf, die in der Datenquelle enthalten sind.  
  
## Syntax  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaEnumSegments`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Ruft die [IEnumVARIANT Interface](http://msdn.microsoft.com/de-de/139e3c93-faef-4003-9079-e0e94494db3e)\-Version dieses Enumerators ab.|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Ruft die Anzahl von Segmenten ab.|  
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Ruft ein Segment mithilfe eines Indexes ab.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Überspringt eine angegebene Anzahl von Segmenten in der Enumerationsfolge.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
  
## Hinweise  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die `QueryInterface`\-Methode für ein [IDiaTable](../../debugger/debug-interface-access/idiatable.md)\-Objekts aufruft.  Weitere Informationen finden Sie im Beispiel für Details.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `IDiaEnumSections`\-Schnittstelle aus einer Tabelle abruft.  Ein ausführlicheres Beispiel finden, die segmenten Anwendung von [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)\-Schnittstelle.  
  
```cpp#  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)