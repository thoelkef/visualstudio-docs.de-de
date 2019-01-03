---
title: Verzeichnisstatuscode-Enumerator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8d6a541415e42e8d35dc4f3ab814c89cf939beb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927609"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-enumerator
Die `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird verwendet, durch die [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Dies wurde in Version 1.2 von die Source-Plug-in-API eingeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Member  
 SCC_DIRSTATUS_INVALID  
 Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Verzeichnis ist nicht unter quellcodeverwaltung.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Verzeichnis befindet sich unter quellcodeverwaltung.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projekt für dieses Verzeichnis ist leer.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)