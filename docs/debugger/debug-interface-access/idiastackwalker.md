---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker-Schnittstelle"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt Methoden bereit, um einen Stackwalk mithilfe der Informationen in der PDB\-Datei zu ermöglichen.  
  
## Syntax  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaStackWalker`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Ruft einen Stapelrahmenenumerator für x86\-Plattformen ab.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Ruft einen Stapelrahmen enumerator für einen bestimmten Plattform des Arrays ab.|  
  
## Hinweise  
 Diese Schnittstelle wird verwendet, um eine Liste der Stapelrahmen für ein geladenes Modul.  Jeder der Methoden wird ein [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)\-Objekt übergeben \(implementiert durch die Clientanwendung\), das die erforderlichen Informationen bereitstellt, um die Liste der Stapelrahmen zu erstellen.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, indem die `CoCreateInstance`\-Methode mit den Klassenbezeichner `CLSID_DiaStackWalker` und die Schnittstellen\-ID von `IID_IDiaStackWalker`aufruft.  Im Beispiel wird gezeigt, wie diese Schnittstelle ermittelt wird.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie die `IDiaStackWalker`\-Schnittstelle abruft.  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)