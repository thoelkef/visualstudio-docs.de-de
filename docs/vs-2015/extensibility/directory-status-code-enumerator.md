---
title: Verzeichnisstatuscode-Enumerator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24f6dde65def4569eb8163d281f872011be0275c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522917"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-Enumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Verzeichnisstatuscode-Enumerator](https://docs.microsoft.com/visualstudio/extensibility/directory-status-code-enumerator).  
  
Die `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird verwendet, durch die [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Dies wurde in Version 1.2 von die Source-Plug-in-API eingeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
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

