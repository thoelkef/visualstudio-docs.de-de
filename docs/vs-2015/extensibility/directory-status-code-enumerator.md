---
title: Verzeichnis Status Code-Enumerator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185257"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-Enumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses im Quell Code Verwaltungssystem angeben. Diese Enumeration wird von [sccdirqueryinfo](../extensibility/sccdirqueryinfo-function.md)verwendet. Dies wurde in Version 1,2 der Quellcodeverwaltungs-Plug-in-API eingeführt.  
  
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
 Der Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Das Verzeichnis befindet sich nicht unter Quell Code Verwaltung.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Das Verzeichnis befindet sich unter Quell Code Verwaltung.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Das Projekt, das diesem Verzeichnis entspricht, ist leer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
