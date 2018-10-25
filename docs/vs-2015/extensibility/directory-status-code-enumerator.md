---
title: Verzeichnisstatuscode-Enumerator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: aaa983b6365e5d8b1c0969b03ebacd5f6b0f8f94
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858510"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnisstatuscode-Enumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

